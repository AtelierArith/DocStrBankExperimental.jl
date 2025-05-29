`Mvp(p::Pol[,v])` は `p` を `Mvp` に変換し、`v` が省略された場合は同じ変数名を使用し、`v` が指定された場合は変数名 `v` を使用します。

```julia-repl
julia> @Pol q
Pol{Int64}: q

julia> Mvp(q^2+q)
Mvp{Int64}: q²+q

julia> Mvp(q^2+q,:x)
Mvp{Int64}: x²+x
```
