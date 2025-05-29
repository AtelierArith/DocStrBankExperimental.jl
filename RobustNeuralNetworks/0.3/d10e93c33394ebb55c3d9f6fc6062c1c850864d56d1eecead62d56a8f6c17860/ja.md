```
WrapREN(ps::AbstractRENParams{T}) where T
```

[注意:] これはレガシーラッパーであり、将来のリリースで削除されます。

直接のパラメータ化からRENラッパーを構築します。

`WrapREN`は、同じオブジェクト内に[`AbstractRENParams`](@ref)と[`ExplicitRENParams`](@ref)を格納する[`REN`](@ref)の代替手段です。これにより、パラメータが更新されるたびに新しい`REN`オブジェクトを作成する必要がなくなります。直接のパラメータが変更された場合、明示的なRENパラメータはユーザーによって更新される必要があります。

`WrapREN`は、`WrapREN`インスタンスを変更することに依存しているため、[`Flux.jl`](http://fluxml.ai/Flux.jl/stable/)では使用できないことに注意してください。

# 例

この例では、いくつかの一般的な動作制約を満たすRENを作成し、モデルパラメータが変更された場合にRENラッパーを更新する方法を示します。

```julia
using LinearAlgebra
using Random
using RobustNeuralNetworks

# セットアップ
rng = Xoshiro(42)
batches = 10
nu, nx, nv, ny = 4, 10, 20, 2

Q = Matrix{Float64}(-I(ny))
R = 0.1^2 * Matrix{Float64}(I(nu))
S = zeros(Float64, nu, ny)

# RENを構築
ren_ps = GeneralRENParams{Float64}(nu, nx, nv, ny, Q, S, R; rng)
ren = WrapREN(ren_ps)

# 一部のダミー入力
x0 = init_states(ren, batches; rng)
u0 = randn(rng, ren.nu, batches)

# 1つのタイムステップでRENを評価
x1, y1 = ren(x0, u0) 

# パラメータを変更した後にモデルを更新
ren.params.direct.B2 .*= rand(rng, size(ren.params.direct.B2)...)
update_explicit!(ren)

println(round(ren.explicit.B2[10];digits=4))

# 出力

-0.0034
```

[`AbstractREN`](@ref)、[`REN`](@ref)、および[`DiffREN`](@ref)も参照してください。
