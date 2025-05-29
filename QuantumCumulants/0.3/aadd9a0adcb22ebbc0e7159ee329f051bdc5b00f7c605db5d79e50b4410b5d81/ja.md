```
cnumber(symbols::Symbol)
cnumber(s::String)
```

記号的な cnumber を作成します。

# 例

```
julia> ps = cnumber(:a)
a

julia> cnumber("a") == ps
true
```
