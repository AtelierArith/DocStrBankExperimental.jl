```
LKJCholesky(k=3, η=1.0)
LKJCholesky(k=3, logη=0.0)
```

`LKJCholesky(k, ...)` は、Cholesky分解として表現された `k×k` LKJ分布（Lewandowski et al 2009）を提供します。特別な場合として、`C = rand(LKJCholesky(k=K, η=1.0))`（または同等に `C=rand(LKJCholesky{k}(k=K, logη=0.0))`）では、`C.L * C.U` はすべての `K×K` 相関行列の集合に対して一様です。ただし、この場合 `C.L` と `C.U` は**一様にサンプリングされていない**ことに注意してください（乗算が非線形であるため）。

この測度の `logdensity` メソッドは、`LowerTriangular`、`UpperTriangular`、または `Diagonal` 行列に適用され、「正しいことを行います」。`logdensity` **は `L*U` が有効な相関行列を生成するかどうかをチェックしません**。

有効な値は $η > 0$ です。$η > 1$ の場合、分布は `I` でピークを持つ単峰性であり、$0 < η < 1$ は谷を生じます。$η = 2$ はあいまいな事前分布として推奨されます。

https://github.com/tpapp/AltDistributions.jl からの適応。
