```
GMRES(; krylovdim=KrylovDefaults.krylovdim[],
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[], 
        orth::Orthogonalizer=KrylovDefaults.orth,
        verbosity=KrylovDefaults.verbosity[])
```

指定されたパラメータを使用してGMRESアルゴリズムのインスタンスを構築します。これは、線形システムを反復的に解決するために`linsolve`に渡すことができます。`GMRES`メソッドは、最大サイズ`krylovdim`のクライロフ部分空間内で最適な`x`を探索し、このプロセスを最大`maxiter`回繰り返すか、`norm(A*x - b) < tol`のときに停止します。クライロフ部分空間を構築する際、`GMRES`は直交化器`orth`を使用します。デフォルトの冗長性レベル`verbosity`は、収束がない場合に警告を印刷することに相当します。

従来の`GMRES`の用語では、パラメータ`krylovdim`は再起動パラメータと呼ばれ、`maxiter`は外部反復の回数、すなわち再起動サイクルの数です。総反復回数、すなわち展開ステップの数は、概ね`krylovdim`と反復回数の積に相当します。

参照: [`linsolve`](@ref), [`BiCG`](@ref), [`BiCGStab`](@ref), [`CG`](@ref), [`LSMR`](@ref), [`MINRES`](@ref)
