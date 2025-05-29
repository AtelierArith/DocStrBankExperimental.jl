```
occupiedsquares(b::Board)
```

ボード上のすべての占有されたマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> occupiedsquares(b) == pieces(b, WHITE) ∪ pieces(b, BLACK)
true

julia> isempty(emptysquares(b) ∩ occupiedsquares(b))
true
```
