```
op(opname::String,sites::Vector{<:Index},n::Int; kwargs...)
```

`sites`配列のn番目のIndexに対する`opname`という名前の演算子に対応するITensorを返します。

# 例

```julia
s = siteinds("S=1/2", 4)
Sz2 = op("Sz", s, 2)
```
