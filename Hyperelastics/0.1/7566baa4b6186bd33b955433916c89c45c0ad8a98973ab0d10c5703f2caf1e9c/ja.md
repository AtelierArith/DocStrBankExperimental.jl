```julia
parameter_bounds(
    _::Hyperelastics.AbstractHyperelasticModel,
    _::Hyperelastics.AbstractHyperelasticTest
) -> NamedTuple{(:lb, :ub), <:Tuple{NamedTuple{(:Gc, :μkT, :κ), <:Tuple{Float64, Float64, Any}}, Nothing}}

```

実験データとモデルが提供されると、パラメータの境界のタプルを返します。

# 引数:

  * `ψ::AbstractHyperelasticModel`: ハイパーエラスティックモデル
  * `test` または `tests`: パラメータの境界を見つけるために使用するテストまたはテストのベクトル。
