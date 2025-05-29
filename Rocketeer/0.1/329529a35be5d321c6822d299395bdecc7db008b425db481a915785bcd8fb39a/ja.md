```julia
apply_kernels(
    rocket::Rocketeer.RocketModule,
    x::AbstractVector{T} where T<:Real
) -> Matrix{Float64}

```

# 概要

ベクトルの [`RocketKernel`](@ref)s をシーケンス `x` に沿って実行します。

# 引数

  * `rocket::RocketModule`: 処理のための多くのカーネルを含むロケットモジュール。
  * `x::RealVector`: ロケット機能を計算するためのデータシーケンス。

# メソッドリスト / 定義場所

```julia
apply_kernels(rocket, x)
```

[`packages/Rocketeer/tbPiD/src/lib/rocket.jl:173`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl) で定義されています。
