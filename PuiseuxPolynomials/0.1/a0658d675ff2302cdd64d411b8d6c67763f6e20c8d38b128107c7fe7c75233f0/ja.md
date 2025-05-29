`Pol(p::Mvp{T}) where T`

は、1変数の `Mvp{T}` `p` を `Pol{T}` に変換します。`p` が1つ以上の変数を持っている場合、またはこの変数が非整数の冪で現れる場合はエラーになります。

```julia-repl
julia> @Mvp x; @Pol q; Pol(x^2+x)
Pol{Int64}: q²+q
```
