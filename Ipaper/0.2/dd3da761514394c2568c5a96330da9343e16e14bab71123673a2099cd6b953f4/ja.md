```
match2(x, y)
```

# 例

```julia
## 元のバージョン
mds = [1, 4, 3, 5]
md = [1, 5, 6]

findall(r_in(mds, md))
indexin(md, mds)

## 現代のバージョン
x = [1, 2, 3, 3, 4]
y = [0, 2, 2, 3, 4, 5, 6]
match2(x, y)
```

# 注意: match2は`y`の要素のみを見つけます
