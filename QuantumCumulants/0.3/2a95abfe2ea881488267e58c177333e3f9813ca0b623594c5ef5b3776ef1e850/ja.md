```
rnumber(symbols::Symbol)
rnumber(s::String)
```

シンボリック rnumber を作成します。

# 例

```
julia> ps = rnumber(:a)
a

julia> rnumber("a") == ps
true
```
