```
make_branch(covariate_idx, layers...)
```

内部関数で、ブランチを作成するために使用されます。より特定のブランチレイヤーを作成することを可能にします。`layers`を次のLux.Chainに追加します：

```julia
Chain(
    SelectDim(1, covariate_idx),
    ReshapeLayer((1,)),
    layers...
)
```

# 引数:

  * `covariate_idx::Union{AbstractVector{<:Int}, Int}`: ブランチで使用する共変量のインデックス。
  * `layers`: ニューラルネットワークを構築するために使用されるレイヤー。
