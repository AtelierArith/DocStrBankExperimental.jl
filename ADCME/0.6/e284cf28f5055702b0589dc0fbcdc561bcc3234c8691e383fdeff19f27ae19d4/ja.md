```
ae_num(output_dims::Array{Int64})
fc_num(output_dims::Array{Int64})
```

ニューラルネットワークの重みとバイアスの数を推定します。最初の次元は特徴次元である必要があります（これは[`ae`](@ref)とは異なり、`ae`では特徴次元を推測できます）、最後の次元は出力次元である必要があります。

# 例

```julia
x = constant(rand(10,30))
θ = ae_init([30, 20, 20, 5])
@assert ae_num([30, 20, 20, 5])==length(θ)
y = ae(x, [20, 20, 5], θ)
```
