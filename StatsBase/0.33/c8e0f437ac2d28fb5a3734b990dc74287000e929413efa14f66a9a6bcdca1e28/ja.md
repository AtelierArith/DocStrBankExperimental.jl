```
fit(Histogram, data[, weight][, edges]; closed=:left, nbins)
```

`data`にヒストグラムをフィットさせます。

# 引数

  * `data`: ベクトル（1次元ヒストグラム用）または同じ長さのベクトルのタプル（*n*次元ヒストグラム用）。
  * `weight`: 各観測値がビンに寄与する重みを示すオプションの`AbstractWeights`（データベクトルと同じ長さ）。重みベクトルが提供されない場合、各観測値の重みは1です。
  * `edges`: 各次元に沿ったビンのエッジを与えるベクトル（通常は`AbstractRange`オブジェクト）またはベクトルのタプル。エッジが提供されない場合、これらはデータから決定されます。

# キーワード引数

  * `closed`: `:left`（デフォルト）の場合、ビンの区間は左閉区間[a,b); `:right`の場合、区間は右閉区間(a,b]です。
  * `nbins`: `edges`引数が提供されない場合、各次元に沿って使用するビンの近似数（単一の整数または整数のタプルのいずれか）。

# 例

```julia
# 一変量
h = fit(Histogram, rand(100))
h = fit(Histogram, rand(100), 0:0.1:1.0)
h = fit(Histogram, rand(100), nbins=10)
h = fit(Histogram, rand(100), weights(rand(100)), 0:0.1:1.0)
h = fit(Histogram, [20], 0:20:100)
h = fit(Histogram, [20], 0:20:100, closed=:right)

# 多変量
h = fit(Histogram, (rand(100),rand(100)))
h = fit(Histogram, (rand(100),rand(100)),nbins=10)
```
