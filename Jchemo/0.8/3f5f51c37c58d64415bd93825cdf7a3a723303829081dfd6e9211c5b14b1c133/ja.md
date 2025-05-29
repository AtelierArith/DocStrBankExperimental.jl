```
getknn(Xtrain, X; metric = :eucl, k = 1)
```

各行のクエリ `X` に対して、`Xtrain` の k 最近傍を返します。

  * `Xtrain` : トレーニング X データ。
  * `X` : クエリ X データ。

キーワード引数:

  * `metric` : クエリに使用される距離のタイプ。可能な値は `:eucl` (ユークリッド)、`：mah` (マハラノビス)、`：sam` (スペクトル角距離)、`：cor` (相関距離) です。
  * `k` : 返す近傍の数。

距離（平方ではない）も返されます。

2つのベクトル x と y の間のスペクトル角距離と相関距離:

  * スペクトル角距離 (x, y) = acos(x'y / normv(x)normv(y)) / pi
  * 相関距離 (x, y) = sqrt((1 - cor(x, y)) / 2)

両方の距離は 0 (y = x) と 1 (y = -x) の間に制限されています。

## 例

```julia
using Jchemo
Xtrain = rand(5, 3)
X = rand(2, 3)
x = X[1:1, :]

k = 3
res = getknn(Xtrain, X; k)
res.ind  # インデックス
res.d    # 距離

res = getknn(Xtrain, x; k)
res.ind

res = getknn(Xtrain, X; metric = :mah, k)
res.ind
```
