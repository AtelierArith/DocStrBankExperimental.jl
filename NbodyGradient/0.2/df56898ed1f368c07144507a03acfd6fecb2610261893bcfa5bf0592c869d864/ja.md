```
TransitParameters(tmax, ic; ti)
```

[`TransitParameters`](@ref)型のコンストラクタ。

# 引数

  * `tmax::T` : 予想される総経過積分時間。（それに応じて配列を割り当てます）
  * `ic::ElementsIC{T}` : 系の初期条件

## オプション

  * `ti::Int64=1` : トランジットが測定される天体のインデックス。（デフォルトは中心天体）
