```
x, w = legendregauss(T, n, endpoint::EndPoint=OneDimensionalNodes.NeitherEndPoint())
```

`-1 < x < 1` の区間に対する `n` 点ガウス・レジェンドル法の点 `x` と重み `w` を返します。重み関数は `w(x) = 1` です。

左ラデュー、右ラデュー、またはロバット法のためには、それぞれ `endpoint=LeftEndPoint()`、`RightEndPoint()` または `BothEndPoints()` を使用してください。
