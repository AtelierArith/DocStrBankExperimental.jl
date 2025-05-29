```
PrecomputedRidgeRegressionSlope
```

事前計算された [リッジ回帰](https://en.wikipedia.org/wiki/Ridge_regression) 行列を含む構造体です。一度 `rrslope::PrecomputedRidgeRegressionSlope` が初期化されると、次のように適用することで `x::AbstractVector` のリッジ回帰傾きを取得するための関数として使用できます：

```julia
rrslope(x)
```
