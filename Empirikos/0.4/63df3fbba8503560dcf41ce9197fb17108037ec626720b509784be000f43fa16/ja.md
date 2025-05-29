```
ccdf(prior::Distribution, Z::EBayesSample)
```

与えられた `prior` $G$ と `EBayesSample` $Z$ に対して、`response(Z)` での $Z$ の周辺分布の補完CDFを評価します。
