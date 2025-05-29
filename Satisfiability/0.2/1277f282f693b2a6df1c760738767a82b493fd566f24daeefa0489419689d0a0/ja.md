```
@satvariable(z, Bool)
@satvariable(a[1:n], Int)
@satvariable(b, BitVector, 32)
```

SAT変数を名前zで構築し、オプションの配列次元と指定された型（`Bool`、`Int`、`Real`または`BitVector`）を指定します。いくつかはオプションの3番目のパラメータを必要とします。

1次元および2次元の変数配列は、次の構文で構築できます。結果はネイティブのJulia配列になります。

```julia
@satvariable(a[1:n], Int) # 長さnのIntベクトル
@satvariable(x[1:m, 1:n], Real) # m x nのInt行列
```
