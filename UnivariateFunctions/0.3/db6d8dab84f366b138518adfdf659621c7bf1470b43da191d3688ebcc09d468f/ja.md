```
create_ols_approximation(y::Vector{<:Real}, x::Vector{<:Real}, base_x::Real = 0.0, degree::Integer = 1, intercept::Bool = true)
create_ols_approximation(y::Vector{<:Real}, x::Union{Vector{DateTime},Vector{Date},Vector{Union{Date,DateTime}}}, base_x::Union{Date,DateTime} = global_base_date, degree::Integer = 1, intercept::Bool = true)
```

OLSによって計算された近似関数。

### 入力

  * `y` - y座標を持つ`Vector`
  * `x` - x座標を持つ`Vector`
  * `base_x` - xをオフセットする実数。したがって、x値が2.0の座標は、base_xが0.2の場合、1.8に変換されます。
  * `degree` - xの最高次数。これが3の場合、方程式にはx、x^2、x^3が予測因子として含まれます。
  * `intercept` - x切片は必要か。

### 戻り値

  * 近似関数を含む`Sum_Of_Functions`。
