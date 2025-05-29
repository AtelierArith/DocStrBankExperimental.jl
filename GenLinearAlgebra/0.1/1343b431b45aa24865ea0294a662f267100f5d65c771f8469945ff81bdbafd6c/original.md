`symmetric_power(m,n)`

returns the `n`-th symmetric power of the square matrix `m`, in the basis  naturally indexed by the `multisets` of `1:n`, where `n=size(m,1)`.

```julia-repl
julia> m=[1 2;3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> Int.(symmetric_power(m,2))
3×3 Matrix{Int64}:
 1   2   4
 6  10  16
 9  12  16
```
