```
NelderMeadSimplex
```

Nelder-Meadアルゴリズムのための単体。

# コンストラクタ

```
NelderMeadSimplex(M::AbstractManifold)
```

多様体`M`から$n+1$のランダムな点を使用して単体を構築します。ここで、$n$は`M`の多様体次元です。

```
NelderMeadSimplex(
    M::AbstractManifold,
    p,
    B::AbstractBasis=DefaultOrthonormalBasis();
    a::Real=0.025,
    retraction_method::AbstractRetractionMethod=default_retraction_method(M, typeof(p)),
)
```

基底`B`から単体を構築し、1つの点が`p`であり、他の点は点`p`での接空間の基底`B`によって定義された各主方向に沿って`a`だけ移動することによって構築されます。これは、ユークリッドNelder-Meadアルゴリズムで初期単体が構築される方法と似ていますが、点`p`での接空間内で行われます。
