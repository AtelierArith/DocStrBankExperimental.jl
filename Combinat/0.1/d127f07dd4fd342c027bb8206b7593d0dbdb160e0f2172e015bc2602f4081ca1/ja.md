`conjugate_partition(λ)`

は、分割 `λ` の共役分割を返します。つまり、`λ` のヤング図の転置を持つ分割です。

```julia-repl
julia> conjugate_partition([4,2,1])
4-element Vector{Int64}:
 3
 2
 1
 1

julia> conjugate_partition([6])
6-element Vector{Int64}:
 1
 1
 1
 1
 1
 1
```
