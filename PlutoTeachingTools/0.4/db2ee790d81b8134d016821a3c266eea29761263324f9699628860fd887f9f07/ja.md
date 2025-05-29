```
Columns(cols...; widths, gap)
```

Plutoで（任意の数の）列をきれいに表示します。

  * `widths` は100に合計する必要があります
  * `gap` はパーセントで指定します

### 例

```julia
# 三つの列
Columns(
    almost(md"ここ"),
    almost(md"そこ"),
    md"ばらばらばら"
)

# カスタマイズされた二つの列
Columns(
    almost(md"ここ"), almost(md"そこ"), 
    widths = [40, 60], gap = 2
)
```
