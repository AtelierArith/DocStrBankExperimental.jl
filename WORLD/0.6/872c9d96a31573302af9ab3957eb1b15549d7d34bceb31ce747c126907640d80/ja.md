```julia
dio(x, fs)
dio(x, fs, opt)

```

Dioはモノラル入力信号に基づいてF0軌道を推定します。

**パラメータ**

  * `x`  : 入力信号
  * `fs` : サンプリング周波数
  * `opt` : DioOption

**戻り値**

  * `time_axis`  : 時間位置。
  * `f0`         : F0輪郭。
