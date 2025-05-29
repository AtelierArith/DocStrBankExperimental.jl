```
dummy(y)
```

カテゴリ変数からダミーテーブルを計算します。

  * `y` : カテゴリ変数。

出力 `Y`（ダミーテーブル）は BitMatrix です。

## 例

```julia
using Jchemo

y = ["d", "a", "b", "c", "b", "c"]
#y =  rand(1:3, 7)
res = dummy(y)
@names res
res.Y
```
