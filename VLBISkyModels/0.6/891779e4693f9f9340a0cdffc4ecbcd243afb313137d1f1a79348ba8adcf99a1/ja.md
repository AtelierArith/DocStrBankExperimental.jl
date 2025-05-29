```
PolExp2Map(a, b, c, d, grid::AbstractRectiGrid)
```

偏極強度マップモデルを、[Arras 2021 (Thesis)](https://www.philipp-arras.de/assets/dissertation.pdf)の行列指数表現を使用して構築します。

各ストークスパラメータは次のようにパラメータ化されます。

```
I = exp(a)cosh(p)
Q = exp(a)sinh(p)b/p
U = exp(a)sinh(p)c/p
V = exp(a)sinh(p)d/p
```

ここで、`a,b,c,d`は条件のない実数であり、`p=√(a² + b² + c²)`です。
