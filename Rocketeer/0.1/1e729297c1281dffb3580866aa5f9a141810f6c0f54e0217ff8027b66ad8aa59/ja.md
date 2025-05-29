```julia
load_rocket() -> Any
load_rocket(filepath::AbstractString) -> Any

```

# 概要

既存のパラメータを持つ [`RocketModule`](@ref) を `.jld2` ファイルからロードして返します。

# 引数

  * `filepath::AbstractString`: デフォルトは `rocket.jld2`、ロケットパラメータを含む `.jld2` へのパス。

# メソッドリスト / 定義場所

```julia
load_rocket()
load_rocket(filepath)
```

[`packages/Rocketeer/tbPiD/src/lib/rocket.jl:210`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl) で定義されています。
