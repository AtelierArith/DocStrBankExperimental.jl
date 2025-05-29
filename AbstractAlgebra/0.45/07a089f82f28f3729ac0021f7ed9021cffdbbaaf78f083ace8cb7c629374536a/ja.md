```
rank(M::MatrixElem{T}) where {T <: RingElement}
```

行列 $M$ のランクを返します。

# 例

```jldoctest
julia> A = QQ[1 2; 3 4];

julia> d = rank(A)
2
```
