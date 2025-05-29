```
melt_list(list; deepcopy=false, kw...)
```

# 引数

  * `list`: DataFrameのリスト

# 例

```julia
d = data.table(; x=1, y=2)
l = [d, d, d, d]

r1 = melt_list(l, id=1:4) # id all is 4
r2 = melt_list(l, id=1:4, deepcopy=true)

melt_list(l; a = 1, b = 2)
```
