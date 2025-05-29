`degrees(W::ComplexReflectionGroup)`

は、`W` が作用するベクトル空間 `V` 上の反射群としての `W` の次数を保持するリストを返します。これらは、`W` の基本不変量の次数 `d₁,…,dₙ` であり、ここで `n` は `V` の次元です。これらは `W` のさまざまな特性を反映しており、特にその積は `W` の基数です。

```julia-repl
julia> W=complex_reflection_group(30)
H₄

julia> degrees(W)
4-element Vector{Int64}:
  2
 12
 20
 30

julia> length(W)
14400
```
