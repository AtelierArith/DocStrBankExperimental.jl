```
aggstat(X, y; algo = mean)
aggstat(X::DataFrame; varx, vary, algo = mean)
```

データセット内のクラスごとの列ごとの統計を計算します。

  * `X` : データ (n, p)。
  * `y` : カテゴリ変数 (n) (クラスメンバーシップ)。
  * `algo` : 計算する関数 (デフォルト = mean)。

データフレームに特有のもの：

  * `varx` : 要約する変数の名前 (ベクトル)。
  * `vary` : クラスごとの計算に考慮するカテゴリ変数の名前 (ベクトル)。

`varx` と `vary` に定義された変数は、`X` の列でなければなりません。

## 例

```julia
using Jchemo, DataFrames, Statistics

n, p = 20, 5
X = rand(n, p)
df = DataFrame(X, :auto)
y = rand(1:3, n)
res = aggstat(X, y; algo = sum)
@names res
res.lev 
res.X
aggstat(df, y; algo = sum).X

n, p = 20, 5
X = rand(n, p)
df = DataFrame(X, string.("v", 1:p))
df.y1 = rand(1:2, n)
df.y2 = rand(["a", "b", "c"], n)
df
aggstat(df; varx = [:v1, :v2], vary = [:y1, :y2], algo = var)  # データフレームを返す 
```
