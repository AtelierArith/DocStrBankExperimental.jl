```
pells_eqn(D::Integer, N::Integer=1)
```

Returns an iterator that yields all nonnegative integer solutions `(x, y)` of the equation

`x^2 - D⋅y^2 = N`.

The eltype of pells_eqn is always `Tuple{BigInt,BigInt}`.

!!! note
    There are often an infinite number of nonnegative solutions to Pell's equation, thus the iterator can have infinite length.


```
julia> using .Iterators

julia> collect(take(pellseqn(2), 5))
5-element Vector{Tuple{BigInt, BigInt}}:
 (3, 2)
 (17, 12)
 (99, 70)
 (577, 408)
 (3363, 2378)

julia> collect(take(pellseqn(2, 1), 5))
5-element Vector{Tuple{BigInt, BigInt}}:
 (3, 2)
 (17, 12)
 (99, 70)
 (577, 408)
 (3363, 2378)

julia> collect(take(pellseqn(5, -1), 5))
5-element Vector{Tuple{BigInt, BigInt}}:
 (2, 1)
 (38, 17)
 (682, 305)
 (12238, 5473)
 (219602, 98209)

julia> collect(take(pellseqn(4, 25), 5))
2-element Vector{Tuple{BigInt, BigInt}}:
 (5, 0)
 (13, 6)

julia> collect(take(pellseqn(4, 10), 5))
Tuple{BigInt, BigInt}[]

julia> collect(take(pellseqn(921, -12), 5))
5-element Vector{Tuple{BigInt, BigInt}}:
 (123013602, 4053436)
 (620494807415610916348542, 20445999054572056617484)
 (3129847429634131057287425640460782483138, 103131979224431202543397867947637928044)
 (15787311699815721226111492312624904230758974206686324318, 520209607285982995690281237198588485553526346187087196)
 (79633022474924155281204153475574155565247711565894067613899610557324322, 2623997304693724359853375113257533978570443685138259398969894101570076)
```
