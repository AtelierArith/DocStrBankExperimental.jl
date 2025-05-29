```
Lanczos(; krylovdim=KrylovDefaults.krylovdim[],
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[],
        orth=KrylovDefaults.orth,
        eager=false,
        verbosity=KrylovDefaults.verbosity[])
```

Krylov部分空間を構築するためのLanczosアルゴリズムを表します。線形演算子が実対称または複素エルミートであると仮定します。`eigsolve`や`exponentiate`で使用できます。対応するアルゴリズムは、サイズが最大`krylovdim`のKrylov部分空間を構築し、最大`maxiter`回繰り返され、Lanczos因子分解の残差のノルムが`tol`より小さくなると停止します。直交化器`orth`は、異なるKrylovベクトルを直交化するために使用されます。`eager=true`で選択されたイagerモードは、このLanczosプロセスを使用するアルゴリズム（例：`eigsolve`）が、次元`krylovdim`の総Krylov部分空間が構築される前に計算を完了しようとすることを意味します。デフォルトの冗長性レベル`verbosity`は、収束がない場合に警告を印刷することに相当します。

非対称または非エルミート線形演算子には`Arnoldi`を使用してください。

関連項目：`factorize`、`eigsolve`、`exponentiate`、`Arnoldi`、`Orthogonalizer`
