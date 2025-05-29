`symmetric_power(m,n)`

は、`m` の `n` 番目の対称冪を返します。これは、`1:n` の `multisets` に自然にインデックス付けされた基底において行われます。ここで、`n=size(m,1)` です。

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
