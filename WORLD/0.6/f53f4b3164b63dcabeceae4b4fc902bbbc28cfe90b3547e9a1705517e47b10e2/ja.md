```julia
cheaptrick(x, fs, timeaxis, f0; opt)

```

CheapTrickは、CheapTrickによって推定されたスペクトルエンベロープで構成されるスペクトログラムを計算します。

**パラメータ**

  * `x` : 入力信号
  * `fs` : サンプリング周波数
  * `time_axis` : 時間軸
  * `f0` : F0コンター
  * `opt` : CheapTrickオプション

**戻り値**

  * `spectrogram`  : CheapTrickによって推定されたスペクトログラム。
