```
BiCGStab(; maxiter=KrylovDefaults.maxiter[], tol=KrylovDefaults.tol[], verbosity=KrylovDefaults.verbosity[])

指定されたパラメータを持つ双共役勾配アルゴリズムのインスタンスを構築します。
これは、線形システム一般線形マップを反復的に解くために`linsolve`に渡すことができます。`BiCGStab`メソッドは、最大サイズ`maxiter`のクライロフ部分空間で最適な`x`を探索するか、`norm(A*x - b) < tol`のときに停止します。デフォルトの冗長性レベル`verbosity`は、収束がない場合に警告を印刷することに相当します。
```

See also: [`linsolve`](@ref), [`GMRES`](@ref), [`CG`](@ref), [`BiCG`](@ref), [`LSMR`](@ref), [`MINRES`](@ref)
