```
create_constant_interpolation_to_left(x::Vector{Date},y::Vector{<:Real})
create_constant_interpolation_to_left(x::Vector{<:Real},y::Vector{<:Real})
create_constant_interpolation_to_left(x::Union{Vector{D},Vector{<:DatePeriod}},y::Vector{<:Real}) where D<:DatePeriod
```

右側の値が左側にコピーされる区分定数補間関数を作成します。

### 入力

  * `x` - x座標を持つ `Vector`
  * `y` - y座標を持つ `Vector`

### 戻り値

  * 補間関数を含む `Piecewise_Function`。
