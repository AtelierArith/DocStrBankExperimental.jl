```
flat_values(t::NamedTuple)
```

ネストされた名前付きタプル `t` を木のように見て、元のタプルに現れる順序で葉の値をタプルとして返します。

```julia-repl
julia> t = (X = (x = 1, y = 2), Y = 3);
julia> flat_values(t)
(1, 2, 3)
```
