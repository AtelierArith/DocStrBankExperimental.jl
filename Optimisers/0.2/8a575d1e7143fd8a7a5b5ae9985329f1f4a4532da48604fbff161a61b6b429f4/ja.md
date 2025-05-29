```
AccumGrad(n::Int)
```

`OptimiserChain(AccumGrad(n), Rule())` で構築されたルールは、これらの `n` 勾配の平均に `Rule` を適用する前に、 `n` ステップの間蓄積します。

これは、利用可能なメモリに対して効果的なバッチサイズが大きすぎる場合のトレーニングに役立ちます。一度にバッチサイズ `b` の勾配を計算する代わりに、サイズ `b/n` の勾配を計算し、 `n` 個のその勾配を蓄積します。

# 例

```jldoctest
julia> m = (x=[1f0], y=[2f0]);

julia> r = OptimiserChain(AccumGrad(2), WeightDecay(0.01), Descent(0.1));

julia> s = Optimisers.setup(r, m);

julia> Optimisers.update!(s, m, (x=[33], y=[0]));

julia> m  # モデルはまだ変更されていない
(x = Float32[1.0], y = Float32[2.0])

julia> Optimisers.update!(s, m, (x=[0], y=[444]));

julia> m  # n=2 の勾配が一度に適用された
(x = Float32[-0.651], y = Float32[-20.202])
```
