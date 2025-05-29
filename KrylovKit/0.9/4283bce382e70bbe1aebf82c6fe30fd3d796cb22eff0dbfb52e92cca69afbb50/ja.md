```
CG(; maxiter=KrylovDefaults.maxiter[], tol=KrylovDefaults.tol[], verbosity=KrylovDefaults.verbosity[])
```

指定されたパラメータを使用して共役勾配アルゴリズムのインスタンスを構築します。これは、正定値（したがって対称またはエルミート）係数行列または演算子を持つ線形システムを反復的に解決するために`linsolve`に渡すことができます。`CG`メソッドは、最大サイズ`maxiter`のクリロフ部分空間で最適な`x`を探索するか、`norm(A*x - b) < tol`のときに停止します。デフォルトの冗長性レベル`verbosity`は、収束がない場合に警告を印刷することに相当します。

参照: [`linsolve`](@ref), [`MINRES`](@ref), [`GMRES`](@ref), [`BiCG`](@ref), [`LSMR`](@ref), [`BiCGStab`](@ref)
