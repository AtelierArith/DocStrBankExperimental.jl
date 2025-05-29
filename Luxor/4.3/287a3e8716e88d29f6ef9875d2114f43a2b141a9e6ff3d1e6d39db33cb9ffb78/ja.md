```
polybspline(controlpoints::Vector{Point}, npoints; degree=3, clamped=true)
```

与えられた制御点のセットからBスプライン曲線を生成します。

# 引数

  * `controlpoints::Vector{Point}`: Bスプラインを定義する制御点の配列。
  * `npoints=100`: Bスプライン曲線上に生成する点の数。
  * `degree=3`: Bスプラインの次数。デフォルトは3。
  * `clamped=true`: Bスプラインがクランプされているかどうかを示すブール値。デフォルトはtrue。

# 戻り値

  * Bスプライン曲線上の点の配列。
