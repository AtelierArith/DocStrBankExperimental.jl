```
GKL(; krylovdim=KrylovDefaults.krylovdim[],
    maxiter=KrylovDefaults.maxiter[],
    tol=KrylovDefaults.tol[],
    orth=KrylovDefaults.orth,
    eager=false,
    verbosity=KrylovDefaults.verbosity[])
```

一般的な行列または線形演算子のためのKrylovのような因子分解を逐次的に構築するためのGolub-Kahan-Lanczos二重対角化アルゴリズムを表します。`svdsolve`で使用できます。対応するアルゴリズムは、サイズが最大`krylovdim`のKrylov部分空間を構築し、最大`maxiter`回繰り返され、Arnoldi因子分解の残差のノルムが`tol`より小さくなると停止します。直交化器`orth`は、異なるKrylovベクトルを直交化するために使用されます。デフォルトの冗長性レベル`verbosity`は、収束がない場合に警告を印刷することに相当します。

関連情報: [`svdsolve`](@ref), [`Orthogonalizer`](@ref)
