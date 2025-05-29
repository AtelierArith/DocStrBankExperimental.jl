`conjugates(c)`

は、`c` の異なるガロア共役のリストを返します（有理数の下で）、`c` から始まります。

```julia-repl
julia> conjugates(1+root(5))
2-element Vector{Cyc{Int64}}:
 1+√5
 1-√5
```
