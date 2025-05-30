```
move_detect(::Solei, x::AbstractVector; kwargs...)
```

動き検出を実装します。これは、2017年の「Movement Detection with Adaptive Window Length for Unobtrusive Bed-based Pressure-Sensor Array」に基づいています。著者はSoleimaniです。

# 引数:

  * `L` : moving_statsのためのウィンドウの長さ。
  * `α=-0.029` : オフセットのための初めの差分の閾値。
  * `κ=3` : 制御信号の大きさ。
  * `min_samples=2` : 動きと見なされるために必要な最小サンプル数。
  * `height=50` : 被験者の身長（cm）。ρ計算における体重の影響を打ち消すためのデフォルト値。
  * `weight=50` : 被験者の体重（kg）。ρ計算における身長の影響を打ち消すためのデフォルト値。
