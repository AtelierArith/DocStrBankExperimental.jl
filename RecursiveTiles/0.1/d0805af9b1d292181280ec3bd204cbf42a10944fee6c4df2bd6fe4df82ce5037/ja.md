```
findrange(f, A::AbstractArray)
```

`isequal(f(A[i₀]), f(A[i₀+δ]))` が真である範囲を見つけます。検索は `i₀=firstindex(A)` から始まり、δ = 0,…,lastindex(A)-1 を通じて進みます。

# 例

```jldoctest
julia> findrange(x -> x < 3 ? 1 : 0, 1:4)
1:2

julia> findrange(abs, -1:2:2)
1:2

julia> findrange(signbit, -5:5)
1:5
```
