```
ProjectedTo(::Type{T}, dims...; conditioner = nothing, parameters = DefaultProjectionParameters)
```

指数族分布への射影の仕様です。

以下の引数は必須です：

  * `Type{T}`: 射影する指数族メンバーの型、例：`Beta`
  * `dims...`: 分布の次元、例：`2` は `MvNormal` のためのものです

以下の引数はオプションです：

  * `conditioner = nothing`: 射影に使用するコンディショナー、すべての指数族メンバーがコンディショナーを必要とするわけではありませんが、いくつかは必要です、例：`Laplace`
  * `parameters = DefaultProjectionParameters`: 射影手続きのためのパラメータ
  * `kwargs = nothing`: `Manopt.gradient_descent!` に渡される追加の引数（オプション）。`gradient_descent!` パラメータの詳細については、[Manopt.jl documentation](https://manoptjl.org/stable/solvers/gradient_descent/#Manopt.gradient_descent)を参照してください。`project_to` に渡される `kwargs` は、パラメータに指定された `kwargs` よりも優先されます。

```jldoctest
julia> using ExponentialFamily

julia> projected_to = ProjectedTo(Beta)
ProjectedTo(Beta)

julia> projected_to = ProjectedTo(Beta, parameters = ProjectionParameters(niterations = 10))
ProjectedTo(Beta)

julia> projected_to = ProjectedTo(MvNormalMeanCovariance, 2)
ProjectedTo(MvNormalMeanCovariance, dims = 2)

julia> projected_to = ProjectedTo(Laplace, conditioner = 2.0)
ProjectedTo(Laplace, conditioner = 2.0)
```
