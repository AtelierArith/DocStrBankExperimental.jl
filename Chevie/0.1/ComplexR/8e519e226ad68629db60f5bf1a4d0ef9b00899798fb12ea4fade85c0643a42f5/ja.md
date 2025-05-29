`codegrees(W::ComplexReflectionGroup)`

は、`reflrep(W)` の空間 `V` 上の反射群としての `W` のコーデグリをベクトルとして返します。これらは、`SV⊗ V^vee` 上の `W` の基本的な導関数の次数よりも1少ないです。

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> codegrees(W)
2-element Vector{Int64}:
 0
 2
```
