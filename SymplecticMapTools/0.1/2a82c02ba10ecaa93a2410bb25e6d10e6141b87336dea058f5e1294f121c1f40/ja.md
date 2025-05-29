```
circle_linear!(z::FourierCircle, FJ::Function, x::AbstractArray, h::Number)
```

`z`のフーリエ係数を安定した周期軌道に関する線形化を用いて埋めます。継続のシードに便利です。

引数:

  * `z`: 不変円
  * `FJ`: マップとその導関数を返す関数 `F, dFdx = FJ(x)`
  * `x`: `F`の周期軌道
  * `h`: 最初の線形化された不変円の平均半径
