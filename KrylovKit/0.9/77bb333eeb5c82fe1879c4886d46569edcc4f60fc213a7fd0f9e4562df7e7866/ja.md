```
LSMR(; krylovdim=1,
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[], 
        orth::Orthogonalizer=ModifiedGramSchmidt(),
        verbosity=KrylovDefaults.verbosity[])
```

LSMRアルゴリズムを表し、$\|Ax - b\|^2 + \|λx\|^2$をユークリッドノルムで最小化します。複数の解が存在する場合、最小ノルム解が返されます。この手法は、Golub-Kahanの二重対角化プロセスに基づいています。これは、通常の方程式$(A^*A + λ^2I)x = A^*b$にMINRESを適用することと代数的に同等ですが、特に$A$が条件が悪い場合に、数値的特性が優れています。

`LSMR`メソッドは、最大サイズ`maxiter`のクリロフ部分空間で最適な$x$を探索するか、または$norm(A'*(A*x - b) + λ^2 * x) < tol$のときに停止します。この場合、パラメータ`krylovdim`は、そのサイズの部分空間が構築されることを示すのではなく、次のベクトルが再直交化される最近のベクトルの数を表します。デフォルトの冗長性レベル`verbosity`は、収束がない場合に警告を印刷することに相当します。

参照: [`lssolve`](@ref)
