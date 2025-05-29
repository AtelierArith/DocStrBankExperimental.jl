```
OptimiserChain(opts...)
```

一連の最適化手法を構成し、`opts`内の各`opt`が指定された順序で勾配を更新します。

空のシーケンスでは、`OptimiserChain()`は恒等的であり、`update!`はパラメータから全勾配を引きます。これは`Descent(1)`と同等です。

# 例

```jldoctest
julia> o = OptimiserChain(ClipGrad(1.0), Descent(0.1));

julia> m = (zeros(3),);

julia> s = Optimisers.setup(o, m)
(Leaf(OptimiserChain(ClipGrad(1.0), Descent(0.1)), (nothing, nothing)),)

julia> Optimisers.update(s, m, ([0.3, 1, 7],))[2]  # 割引前にクリップ
([-0.03, -0.1, -0.1],)
```
