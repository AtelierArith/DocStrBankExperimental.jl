```
FastForest(p, nkeys=2; stat=FitNormal(), kw...)
```

各変数が `stat` によって要約されるランダムフォレストを計算します。

# キーワード引数

  * `nt=100`: フォレスト内の木の数
  * `b=floor(Int, sqrt(p))`: 各木が受け取るランダム特徴の数
  * `maxsize=1000`: フォレスト内の任意の木の最大サイズ
  * `splitsize=5000`: 分割前の任意のノード内の観測数
  * `λ = 5 * (1 / nt)`: 各木が新しい観測で更新される確率

# 例

```
x, y = randn(10^5, 10), rand(1:2, 10^5)

o = fit!(FastForest(10), zip(eachrow(x),y))

classify(o, x[1,:])
```
