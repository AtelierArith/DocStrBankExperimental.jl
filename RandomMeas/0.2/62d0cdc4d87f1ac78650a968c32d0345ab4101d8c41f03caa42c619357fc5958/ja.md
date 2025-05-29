```
flatten(O::Union{MPS, MPO, Vector{ITensor}})
```

マトリックス積状態 (MPS)、マトリックス積演算子 (MPO)、またはITensorのベクトルを構成するテンソルを順次掛け合わせて単一のITensorにフラット化します。

# 引数

  * `O`: フラット化されるMPS、MPO、またはITensorのベクトル。

# 戻り値

`O`内の個々のテンソルの積を表すITensor。

# 例

```julia
A = random_mps(siteinds("Qubit", 5))
flatA = flatten(A)
```
