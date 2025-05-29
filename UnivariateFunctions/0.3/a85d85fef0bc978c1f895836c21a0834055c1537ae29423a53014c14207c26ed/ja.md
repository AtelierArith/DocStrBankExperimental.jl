```
create_constant_interpolation_to_right(x::Vector{Date},y::Vector{<:Real})
create_constant_interpolation_to_right(x::Vector{<:Real},y::Vector{<:Real})
create_constant_interpolation_to_right(x::Union{Vector{D},Vector{<:DatePeriod}},y::Vector{<:Real}) where D<:DatePeriod
```

左側の値が右側にコピーされる区分定数補間関数を作成します。

### 入力

  * `x` - x座標を持つ `Vector`
  * `y` - y座標を持つ `Vector`

### 戻り値

  * 補間関数を含む `Piecewise_Function`。
