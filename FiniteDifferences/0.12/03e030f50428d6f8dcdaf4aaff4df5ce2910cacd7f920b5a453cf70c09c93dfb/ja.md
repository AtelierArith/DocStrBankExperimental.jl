```
FiniteDifferenceMethod(
    grid::AbstractVector{Int},
    q::Int;
    condition::Real=DEFAULT_CONDITION,
    factor::Real=DEFAULT_FACTOR,
    max_range::Real=Inf
)
```

有限差分法を構築します。

# 引数

  * `grid::Vector{Int}`: グリッド。[`AdaptedFiniteDifferenceMethod`](@ref) または [`UnadaptedFiniteDifferenceMethod`](@ref) を参照してください。
  * `q::Int`: 推定する導関数の次数。

# キーワード

  * `condition::Real`: 条件数。[`DEFAULT_CONDITION`](@ref) を参照してください。
  * `factor::Real`: ファクター数。[`DEFAULT_FACTOR`](@ref) を参照してください。
  * `max_range::Real=Inf`: 導関数が推定される入力からの最大距離。

# 戻り値

  * `FiniteDifferenceMethod`: 指定された有限差分法。
