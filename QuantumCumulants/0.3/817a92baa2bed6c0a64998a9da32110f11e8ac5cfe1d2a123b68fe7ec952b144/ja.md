```
cnumbers(symbols::Symbol...)
cnumbers(s::String)
```

記号的な cnumbers を作成します。

# 例

```
julia> ps = cnumbers(:a, :b)
(a, b)

julia> cnumbers("a b") == ps
true
```
