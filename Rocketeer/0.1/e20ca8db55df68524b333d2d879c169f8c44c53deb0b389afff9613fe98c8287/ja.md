```julia
save_rocket(rocket::Rocketeer.RocketModule)
save_rocket(
    rocket::Rocketeer.RocketModule,
    filepath::AbstractString
)

```

# 概要

[`RocketModule`](@ref) のパラメータを `.jld2` ファイルに保存します。

# 引数

  * `rocket::RocketModule`: 保存する [`RocketModule`](@ref) 。
  * `filepath::AbstractString`: デフォルトは `rocket.jld2`、ロケットパラメータを保存するための `.jld2` へのパス。

# メソッドリスト / 定義場所

```julia
save_rocket(rocket)
save_rocket(rocket, filepath)
```

[`packages/Rocketeer/tbPiD/src/lib/rocket.jl:196`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl) で定義されています。
