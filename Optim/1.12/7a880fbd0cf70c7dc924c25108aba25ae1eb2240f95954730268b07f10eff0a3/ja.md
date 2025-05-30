# Fminbox

## コンストラクタ

```julia
Fminbox(method;
        mu0=NaN,
        mufactor=0.0001,
        precondprep(P, x, l, u, mu) -> precondprepbox!(P, x, l, u, mu))
```

## 説明

Fminboxは、単純な境界（またはボックス制約）を持つ最適化のためのプライマルバリア法を実装しています。ここで実装されているアプローチに非常に近い説明は、NocedalとWrightの第19.6節に見つけることができます（sec. 19.6, 2006）。

## 参考文献

  * Wright, S. J. and J. Nocedal (1999), Numerical optimization. Springer Science 35.67-68: 7.
