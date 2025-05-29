```
diagonal_matrix(x::T...) where T <: NCRingElement -> MatElem{T}
diagonal_matrix(x::Vector{T}) where T <: NCRingElement -> MatElem{T}
diagonal_matrix(R::NCRing, x::Vector{T}) where T <: NCRingElement -> MatElem{T}
```

$ x $ の要素が対角成分である対角行列を返します。リング $ R $ が指定されている場合は、作成される行列の成分の親として使用されます。そうでない場合は、ベクトル $ x $ から親が推測されます。

# 例

```jldoctest
julia> diagonal_matrix(ZZ(1), ZZ(2))
[1   0]
[0   2]

julia> diagonal_matrix([ZZ(3), ZZ(4)])
[3   0]
[0   4]

julia> diagonal_matrix(ZZ, [5, 6])
[5   0]
[0   6]
```
