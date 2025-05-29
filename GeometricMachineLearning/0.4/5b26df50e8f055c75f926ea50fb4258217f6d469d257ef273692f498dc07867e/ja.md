```
optimization_step!(o, λY, ps, dx)
```

重み `ps` を [`Optimizer`](@ref)、`cache` および一次導関数 `dx` に基づいて更新します。

`optimization_step!` は内部で [`update!`](@ref) を呼び出します。 `update!` はすべての [`OptimizerMethod`](@ref) に対して実装される必要があります。

# 引数

`optimization_step!` へのすべての引数は必須です：

1. `o::`[`Optimizer`](@ref),
2. `λY::NamedTuple`: この名前付きタプルは `ps` と同じキーを持ちますが、[`GlobalSection`](@ref)s を含みます、
3. `ps::NamedTuple`: ニューラルネットワークのパラメータ、
4. `dx::Union{NamedTuple, NeuralNetworkParameters}`: NamedTuple として格納された勾配。

すべての引数は `NamedTuple` として与えられます。ニューラルネットワークの重みはその形式で格納されています。

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: params

l = StiefelLayer(3, 5)
ps = params(NeuralNetwork(Chain(l), Float32)).L1
cache = apply_toNT(MomentumCache, ps)
o = Optimizer(MomentumOptimizer(), cache, 0, geodesic)
λY = GlobalSection(ps)
dx = (weight = rand(Float32, 5, 3), )

# オプティマイザを呼び出す
optimization_step!(o, λY, ps, dx)

_test_nt(x) = typeof(x) <: NamedTuple

_test_nt(λY) & _test_nt(ps) & _test_nt(cache) & _test_nt(dx)

# 出力

true
```

# 拡張ヘルプ

ここでの導関数 `dx` は通常、損失関数を微分することによって AD ルーチンを介して取得されます。すなわち、`dx` は $\nabla_xL$ です。
