`laurent_denominator(p1,p2,…)`

は、すべてのローレンツ多項式 `p1,p2,…` に対して、各変数において正の次数を持つ積 `m*pᵢ` を持つような、各変数において最小の次数を持つ一意の単項式 `m` を返します。

```julia-repl
julia> laurent_denominator(x^-1,y^-2+x^4)
Monomial{Int64}:xy²
```
