```
tabdupl(x)
```

ベクトル内の重複した値を表形式で表示します。

  * `x` : カテゴリ変数。

## 例

```julia
using Jchemo

x = ["a", "b", "c", "a", "b", "b"]
tab(x)
res = tabdupl(x)
res.keys
res.vals
```
