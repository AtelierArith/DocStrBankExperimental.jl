```
findrange(f, A::AbstractArray)
```

Find the range for which `isequal(f(A[i₀]), f(A[i₀+δ]))` is true; the search starts from `i₀=firstindex(A)` and proceeds through δ = 0,…,lastindex(A)-1.

# Examples

```jldoctest
julia> findrange(x -> x < 3 ? 1 : 0, 1:4)
1:2

julia> findrange(abs, -1:2:2)
1:2

julia> findrange(signbit, -5:5)
1:5
```
