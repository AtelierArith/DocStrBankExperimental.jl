```
KernelParameters
```

抽象型です。

すべての KernelParameters 型は、後で内部関数 `Kf` および `∇Kf` に渡される特定のパラメータを含んでいます。

KernelParameters 型は、例えば `PolynomialKP(X::Matrix{Float64})` または `GaussianKP(X::Matrix{Float64})` を使用して設定されます。
