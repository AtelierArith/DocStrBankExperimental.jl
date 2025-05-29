```
compute_rmsd_minimizer(f::AbstractAtomBijection)
compute_rmsd_minimizer(A::AbstractAtomContainer{T}, B::AbstractAtomContainer{T})
compute_rmsd_miminizer(A::AtomTable{T}, B::AtomTable{T})
```

与えられた原子の対応に対するRMSD最小化剛体変換を計算します。引数が原子コンテナまたはテーブルの場合は、デフォルトで[`TrivialAtomBijection`](@ref)が使用されます。

# サポートされているキーワード引数

  * `minimizer::Type{<: AbstractRMSDMinimizer} = RMSDMinimizerCoutsias` 最適な回転行列を計算するために使用されるメソッド。[`RMSDMinimizerCoutsias`](@ref)および[`RMSDMinimizerKabsch`](@ref)を参照してください。
