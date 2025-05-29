```
create_linear_interpolation(x::Vector{Date},y::Vector{<:Real})
create_linear_interpolation(x::Union{Vector{D},Vector{<:DatePeriod}},y::Vector{<:Real}) where D<:DatePeriod
create_linear_interpolation(x::Vector{R},y::Vector{<:Real}) where R<:Real
```

区分線形補間関数を作成します。これは連続しています。

### 入力

  * `x` - x座標を持つ `Vector`
  * `y` - y座標を持つ `Vector`

### 戻り値

  * 補間関数を含む `Piecewise_Function`。
