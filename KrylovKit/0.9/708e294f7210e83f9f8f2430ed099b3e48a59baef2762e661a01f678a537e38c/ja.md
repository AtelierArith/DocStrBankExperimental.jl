```
Arnoldi(; krylovdim=KrylovDefaults.krylovdim[],
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[],
        orth=KrylovDefaults.orth,
        eager=false,
        verbosity=KrylovDefaults.verbosity[])
```

一般的な行列または線形演算子のためのクリロフ部分空間を構築するためのアーノルディアルゴリズムを表します。`eigsolve`や`exponentiate`で使用できます。対応するアルゴリズムは、サイズが最大`krylovdim`のクリロフ部分空間を構築し、最大`maxiter`回繰り返され、アーノルディ因子分解の残差のノルムが`tol`より小さくなると停止します。直交化器`orth`は、異なるクリロフベクトルを直交化するために使用されます。`eager=true`で選択されたイagerモードは、このアーノルディプロセスを使用するアルゴリズム（例：`eigsolve`）が、次元`krylovdim`の総クリロフ部分空間が構築される前に計算を完了しようとすることを意味します。デフォルトの冗長性レベル`verbosity`は、収束がない場合に警告を印刷することに相当します。

実対称または複素エルミート線形演算子には`Lanczos`を使用してください。

参照：[`eigsolve`](@ref), [`exponentiate`](@ref), [`Lanczos`](@ref), [`Orthogonalizer`](@ref)
