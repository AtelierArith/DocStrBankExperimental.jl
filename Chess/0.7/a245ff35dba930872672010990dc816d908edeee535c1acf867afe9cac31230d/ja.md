```
sidetomove(b::Board)
```

現在の手番、`WHITE` または `BLACK`。

# 例

```julia-repl
julia> b = startboard();

julia> b2 = domove(b, "e4");

julia> sidetomove(b)
WHITE

julia> sidetomove(b2)
BLACK
```
