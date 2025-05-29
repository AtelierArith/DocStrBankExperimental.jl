```julia
isplackettburman(d::Matrix{Int64}) -> Bool

```

To check if  a given design is  a Plackett-Burman design, we must check for the following properties, obtained in the original Plackett-Burman paper:

1. Each component is replicated at each  of its values the same number of times, that is, the sum of elements in each column is zero
2. Each  pair of components  occur together at  every combination of  values the same number of times, that is, the sum of each pair of columns will produce a column with the  same number of occurrences  of $2$ and $-2$,  and twice that number of occurrences of $0$

> Plackett,  R.L. and  Burman, J.P.,  1946. The  design of  optimum multifactorial experiments. Biometrika, 33(4), pp.305-325.


```jldoctest
julia> isplackettburman(plackettburman(2))
true

julia> isplackettburman(plackettburman(4))
true

julia> isplackettburman(plackettburman(16))
true

julia> isplackettburman(rand(Int, 4,4))
false

```
