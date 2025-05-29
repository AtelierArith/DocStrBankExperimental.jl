```julia
synthesis(f0, spectrogram, aperiodicity, period, fs, len)

```

合成は、f0、スペクトログラム、および非周期性に基づいて音声を合成します（励起信号ではありません）。

**パラメータ**

  * `f0` : f0 コンター
  * `spectrogram` : CheapTrick によって推定されたスペクトログラム
  * `aperiodicity` : D4C に基づく非周期性スペクトログラム
  * `period` : 分析に使用される時間的周期
  * `fs` : サンプリング周波数
  * `len` : 出力信号の長さ

**戻り値**

  * `y` : 計算された音声
