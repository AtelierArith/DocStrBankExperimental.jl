`coefficients(c::Cyc)`

導体 `n` の巡回体 `c` に対して、`c==∑ᵢ vᵢ₊₁ ζⁱ` となる長さ `n` のベクトル `v` を返します。ただし、`i∈ 0:n-1` です。

```julia-repl
julia> coefficients(Cyc(E(9)))
9-element Vector{Int64}:
  0
  0
  0
  0
 -1
  0
  0
 -1
  0
```
