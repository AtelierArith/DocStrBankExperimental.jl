```
KeysSplinePrime([T=Float64,] a, B=Flat)
```

は、浮動小数点型 `T`、パラメータ `a` および境界条件 `B` に対する Keys カーネルの 1 次導関数であるカーネルインスタンスを生成します（詳細は [`KeysSpline`](@ref) を参照）。この導関数は次のように与えられます：

```
ker′(x) = p′(abs(x))*sign(x)   もし abs(x) ≤ 1
          q′(abs(x))*sign(x)   もし 1 ≤ abs(x) ≤ 2
          0                    もし abs(x) ≥ 2
```

ここで：

```
p(x) = -2*(a + 3)*x + 3*(a + 2)*x^2
q(x) = 8a - 10a*x + 3a*x^2
```
