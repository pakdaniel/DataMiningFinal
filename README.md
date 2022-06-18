# IEOR E4540 - Data Mining at Columbia University 

## Project 1: Transformers in action
Choose one of the domains we were discussing in the class (audio/speech, images/videos or text) and
conduct an ablation studies (accuracy-wise) of the models trained with the Transformer as a function
of the length of the input sequence. For image/video data you can control the length for the given
input by choosing the (generalized) patch size. If you use audio/speech or text data, target long
input sequences (with tokens corresponding to spectrograms or words) and apply local attention with
varying window length. For long enough input sequences you can apply Performer variant of your
model. Report all the empirical results and describe in detail all the variants you have compared.

## Chosen Dataset
For this project, I chose the Variably Intense Vocalizations of Affect and Emotion Corpus (VIVAE) dataset 
to use various transformer architectures to predict the elicited emotion from the audio. VIVAE consists
of 1085 audio samples recorded at a 44.1-kHz sampling rate and 16-bit resolution. There are 11 unique subjects.
The emotions consists of 6 different options: achievement, anger, fear, pain, pleasure, and surprise.
The emotions also have various intensities: low, moderate, strong, peak.
Due to a having 24 unique combintations of emotions and emotion intensities and only 1085 unique audio samples, the class label was chosen to be 
just the emotion.

## Chosen Metric 
The labels were found to be balanced. Accuracy and AUC were chosen as the metrics to judge how well a model performs.

## Representation of Data
To use the audio recordings as the input to a transformer model, 2 different approaches were taken to represent the data.

1. 1-D representation - Keep the audio as the original time series of various lengths
2. 2-D representation - Transform the 1-D time series into a Mel Spectrogram, a 2-D representation of audio by including temporal and frequency information

## Models
A variety of different models were used.
1. Logistic Regression - Chosen to be a baseline classifier; used 1-D representation 
2. Multi Layer Perceptron - Chosen to be a baseline deep neural network; used 1-D representation
3. Vision Transformer - Used 2-D representation of data with various patch sizes with no pre-training or fine-tuning; model architecture was obtained from https://github.com/lucidrains/vit-pytorch
4. ViT-Base - Used 2-D representation of data following original paper and was already pre-trained and fine-tuned; model architecture was obtained from https://github.com/rwightman/pytorch-image-models
5. wav2vec2 - Used 1-D representation of data following original paper and was already pre-trained and fine-tuned; model architecture was obtained from https://huggingface.co/facebook/wav2vec2-base
