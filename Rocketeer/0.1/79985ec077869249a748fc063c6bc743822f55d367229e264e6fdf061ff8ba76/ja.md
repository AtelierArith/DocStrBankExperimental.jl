```julia
apply_kernel(
    kernel::Rocketeer.RocketKernel,
    x::AbstractVector{T} where T<:Real
) -> Any

```

# 概要

単一の [`RocketKernel`](@ref) をシーケンス `x` に適用します。

# 引数

  * `kernel::RocketKernel`: 特徴を計算するために使用される [`RocketKernel`](@ref)。
  * `x::RealVector`: Rocket 特徴を計算するためのデータシーケンス。

# メソッドリスト / 定義場所

```julia
apply_kernel(kernel, x)
```

[`packages/Rocketeer/tbPiD/src/lib/rocket.jl:136`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl) で定義されています。
