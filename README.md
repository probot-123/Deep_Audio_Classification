# Audio Classification: Capuchinbird Call Detection

This project implements a deep learning model to detect and count Capuchinbird calls in forest audio recordings. The model uses spectrogram-based audio processing and convolutional neural networks to classify audio segments.

## 🎯 Project Overview

The goal is to automatically identify and count the number of Capuchinbird calls present in forest audio recordings. This is useful for wildlife monitoring and biodiversity studies.

## 📁 Project Structure

```
audio_classification/
├── AudioClassification (1).ipynb    # Main Jupyter notebook with the complete workflow
├── results.csv                      # Output file with predictions for each recording
└── README.md                       # This file
```

## 🚀 Features

- **Audio Preprocessing**: Converts audio files to 16kHz mono format and generates spectrograms
- **Deep Learning Model**: CNN-based architecture for binary classification
- **Batch Processing**: Efficient processing of multiple audio files
- **Results Export**: CSV output with call counts for each recording

## 🛠️ Technical Implementation

### Data Processing Pipeline

1. **Audio Loading**: Loads WAV/MP3 files and resamples to 16kHz mono
2. **Spectrogram Generation**: Converts audio to spectrograms using Short-Time Fourier Transform (STFT)
3. **Data Augmentation**: Zero-padding to ensure consistent input dimensions (1491×257×1)
4. **Batch Processing**: Processes audio in batches for efficient training

### Model Architecture

- **Input**: Spectrogram images (1491×257×1)
- **Convolutional Layers**: 2 Conv2D layers with ReLU activation
- **Dense Layers**: 64 units with ReLU, followed by sigmoid output
- **Output**: Binary classification (Capuchinbird call present/absent)

### Training Details

- **Optimizer**: Adam
- **Loss Function**: Binary Crossentropy
- **Metrics**: Precision, Recall
- **Training**: 4 epochs with validation split

## 📊 Results

The model achieves high performance on the validation set:

- **Precision**: ~96%
- **Recall**: ~96%
- **Validation Loss**: ~0.10

The `results.csv` file contains predictions for 100 forest recordings, showing the number of Capuchinbird calls detected in each recording.

## 🎵 Audio Data

The project uses two types of audio data:

- **Positive samples**: Audio clips containing Capuchinbird calls
- **Negative samples**: Audio clips without Capuchinbird calls
- **Test recordings**: 100 forest recordings for prediction

## 📋 Requirements

### Dependencies

- TensorFlow
- TensorFlow I/O
- Matplotlib
- NumPy
- CSV (built-in)

### Installation

```bash
pip install tensorflow tensorflow-io matplotlib numpy
```

## 🔧 Usage

1. **Open the Jupyter notebook**:

   ```bash
   jupyter notebook "AudioClassification (1).ipynb"
   ```

2. **Run the cells sequentially** to:

   - Install dependencies
   - Load and preprocess audio data
   - Train the model
   - Make predictions on test recordings
   - Export results to CSV

3. **View results** in `results.csv`:
   - Each row contains a recording filename and the number of Capuchinbird calls detected


## 📝 Output Format

The `results.csv` file contains:

- `recording`: Filename of the audio recording
- `capuchin_calls`: Number of Capuchinbird calls detected

Example:

```csv
recording,capuchin_calls
recording_16.mp3,3
recording_27.mp3,0
recording_47.mp3,4
```

