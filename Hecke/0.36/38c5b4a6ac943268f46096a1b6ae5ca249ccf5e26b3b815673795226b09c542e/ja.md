```
atkin_modular_polynomial([R::MPolyRing,] n::Int) -> Poly
```

素数レベル $n$ のアトキンモジュラ多項式を $\mathbf{Z}[x, y]$ の要素として返します。オプションの二変数多項式 $R$ が指定されている場合、その多項式は $R$ の変数で評価されます。

アトキンモジュラ多項式はレベル `400` まで利用可能です。
