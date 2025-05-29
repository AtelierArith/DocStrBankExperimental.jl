`reflection_character(W::ComplexReflectionGroup,w)` または `reflchar`

`W` の要素 `w` のトレースを、`W` が作用するベクトル空間 `V` のエンドモルフィズムとして返します。

```julia-repl
julia> W=coxgroup(:B,3)
B₃

julia> reflchar(W,longest(W))
-3
```
