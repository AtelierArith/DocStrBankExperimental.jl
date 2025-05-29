```
classical_modular_polynomial([R::MPolyRing,] n::Int) -> Poly
```

レベル $n$ の古典的なモジュラー多項式を $\mathbf{Z}[x, y]$ の要素として返します。オプションの二変数多項式 $R$ が指定されている場合、その多項式は $R$ の変数で評価されます。

モジュラー多項式はレベル `59` まで利用可能です。
