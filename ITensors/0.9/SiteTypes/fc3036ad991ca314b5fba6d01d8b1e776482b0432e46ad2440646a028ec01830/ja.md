```
ops(s::Vector{<:Index}, os::Vector)
ops(os::Vector, s::Vector{<:Index})
```

演算子のリストが与えられた場合、インデックスのコレクションを使用してITensorを作成します。

# 例

```julia
s = siteinds("Qubit", 4)
os = [("H", 1), ("X", 2), ("CX", 2, 4)]
# gates = ops(s, os)
gates = ops(os, s)
```
