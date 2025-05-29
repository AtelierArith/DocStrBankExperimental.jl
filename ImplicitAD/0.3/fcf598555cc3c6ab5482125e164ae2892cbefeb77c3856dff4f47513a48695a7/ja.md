```
implicit_linear(A, b; lsolve=linear_solve, Af=factorize)
```

暗黙の関数をAD互換にする（特にForwardDiffおよびReverseDiffとの互換性）。このバージョンは線形方程式 $Ay = b$ 用です。

# 引数

  * `A::matrix`, `b::vector`: 線形系の成分 $A y = b$
  * `lsolve::function`: lsolve(A, b)。線形系を解くための関数で、デフォルトはバックスラッシュ演算子です。
  * `Af::factorization`: Aのオプションの因数分解で、デフォルトの因数分解をオーバーライドするのに便利です。また、同じA行列で複数の線形解を実行する場合にも役立ちます。
