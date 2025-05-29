```
rnumbers(symbols::Symbol...)
rnumbers(s::String)
```

記号的な rnumbers を作成します。

# 例

```
julia> ps = rnumbers(:a, :b)
(a, b)

julia> rnumbers("a b") == ps
true
```
