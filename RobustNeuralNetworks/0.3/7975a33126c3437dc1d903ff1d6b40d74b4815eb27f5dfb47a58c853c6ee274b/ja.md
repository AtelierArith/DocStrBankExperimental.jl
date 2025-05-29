```
抽象型 AbstractREN 終わり
```

再帰的平衡ネットワークの明示的パラメータ化。

```
(m::AbstractREN)(xt::AbstractVecOrMat, ut::AbstractVecOrMat)
```

内部状態 `xt` と入力 `ut` を与えて `AbstractREN` モデルを呼び出します。

引数が行列の場合、各列は状態または入力のベクトルでなければなりません（バッチシミュレーションを許可します）。

# 例

この例では、[`ContractingRENParams`](@ref) を使用して収縮する [`REN`](@ref) を作成し、いくつかのランダムに生成された入力でモデルを呼び出します。

```jldoctest
using Random
using RobustNeuralNetworks

# セットアップ
rng = Xoshiro(42)
batches = 10
nu, nx, nv, ny = 4, 2, 20, 1

# REN を構築
contracting_ren_ps = ContractingRENParams{Float64}(nu, nx, nv, ny; rng)
ren = REN(contracting_ren_ps)

# 一部のランダム入力
x0 = init_states(ren, batches; rng)
u0 = randn(rng, ren.nu, batches)

# 一つのタイムステップで REN を評価
x1, y1 = ren(x0, u0)

println(round.(y1;digits=2))

# 出力

[-1.49 0.75 1.34 -0.23 -0.84 0.38 0.79 -0.1 0.72 0.54]
```

さらに [`REN`](@ref)、[`WrapREN`](@ref)、および [`DiffREN`](@ref) を参照してください。
