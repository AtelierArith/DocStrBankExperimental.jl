```
otimes(::Vec)
```

ベクトル自身とのオープン積を計算します。`SymmetricTensor`を返します。

# 例

```jldoctest
julia> A = rand(Vec{2})
2-element Vec{2, Float64}:
 0.32597672886359486
 0.5490511363155669

julia> otimes(A)
2×2 SymmetricTensor{2, 2, Float64, 3}:
 0.106261  0.178978
 0.178978  0.301457
```
