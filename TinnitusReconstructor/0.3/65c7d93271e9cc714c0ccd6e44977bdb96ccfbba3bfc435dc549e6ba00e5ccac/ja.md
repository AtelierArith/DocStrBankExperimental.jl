信号を `0:duration` から切り取り、`duration` は秒単位で、短時間フーリエ変換を計算し、デシベルに変換し、STFTウィンドウを平均化します。

# 引数

  * `audio::Union{AbstractSampleBuf, Matrix}`
  * `duration::Real`: 秒単位の持続時間

# 使用例

```julia
audio = load(audio_file_path)
spect = wav2spect(audio; duration = 1.0)
```
