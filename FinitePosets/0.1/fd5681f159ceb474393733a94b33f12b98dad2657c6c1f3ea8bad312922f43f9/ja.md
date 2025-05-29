`partition(P::CPoset)`

は、`P` に関連付けられた同値関係によって誘導される `1:length(P)` の分割を返します。すなわち、`i` と `j` は、`i<k` および `j<k` となる `k` が同じであり、かつ `k<i` および `k<j` となる `k` が同じである場合、分割の同じ部分に属します。

```julia-repl
julia> p=CPoset([i==j || i%4<j%4 for i in 1:8, j in 1:8])
4,8<1,5<2,6<3,7

julia> partition(p)
4-element Vector{Vector{Int64}}:
 [4, 8]
 [2, 6]
 [3, 7]
 [1, 5]
```

`partition(P::Poset)` は `partition(P.C)` を返します。
