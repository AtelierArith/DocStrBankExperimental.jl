```
LinearSymplecticAttention
```

線形シンプレクティックアテンション層を実装します。[`GradientLayer`](@ref)に類似して、$Q$または$P$部分のみを変更するマッピングを実行します。

この層は*積空間の意味*でシンプレクティシティを保持します。

詳細については、[`LinearSymplecticAttentionQ`](@ref)および[`LinearSymplecticAttentionP`](@ref)を参照してください。

# 実装

[`LinearSymplecticAttention`](@ref)層の係数は[`SymmetricMatrix`](@ref)です：

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: params

l = LinearSymplecticAttentionQ(3, 5)
ps = params(NeuralNetwork(Chain(l))).L1

typeof(ps.A) <: SymmetricMatrix

# output

true
```
