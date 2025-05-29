```
aggmean(X, y)
```

クラスごとの列平均をデータセットで計算します。

  * `X` : データ (n, p)。
  * `y` : カテゴリ変数 (n) (クラスメンバーシップ)。

`aggstat` よりも高速です。

## 例

```julia
using Jchemo

n, p = 20, 5
X = rand(n, p)
y = rand(1:3, n)
df = DataFrame(X, :auto) 
res = aggmean(X, y)
res.X
res.lev 
aggmean(df, y).X
```
