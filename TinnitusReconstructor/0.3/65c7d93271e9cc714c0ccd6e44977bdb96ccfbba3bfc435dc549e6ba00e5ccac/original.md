Crops a signal from `0:duration`, where `duration` is in seconds, computes the short-time Fourier transform, converts to decibels, and then averages across STFT windows.

# Arguments

  * `audio::Union{AbstractSampleBuf, Matrix}`
  * `duration::Real`: duration in seconds

# Example Usage

```julia
audio = load(audio_file_path)
spect = wav2spect(audio; duration = 1.0)
```
