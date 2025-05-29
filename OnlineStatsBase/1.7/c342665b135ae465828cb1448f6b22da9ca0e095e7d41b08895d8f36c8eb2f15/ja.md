```
ExtremeValues(T = Float64, b=25)
```

データストリームの `b` 番目に小さい値と大きい値（およびその値が発生した回数）を追跡します。

# 例

```
o = ExtremeValues(Int, 3)

fit!(o, 1:100)

value(o).lo  # [1 => 1, 2 => 1, 3 => 1]

value(o).hi  # [98 => 1, 99 => 1, 100 => 1]
```
