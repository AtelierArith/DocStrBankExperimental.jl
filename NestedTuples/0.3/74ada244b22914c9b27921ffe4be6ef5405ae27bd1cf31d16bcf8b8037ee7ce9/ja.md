```
randnt(width::Int, depth::Int)
```

幅 `width` と深さ `depth` の葉に `Symbol` があるランダムなネストされた NamedTuple を構築します。

例:

```
julia> randnt(3,2)
(a = (y = :y, r = :r, p = :p), v = (f = :f, e = :e, v = :v))
```
