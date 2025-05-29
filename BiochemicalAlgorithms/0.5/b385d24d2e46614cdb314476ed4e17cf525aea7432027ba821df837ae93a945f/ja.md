```
map_rigid!(f::AbstractAtomBijection)
map_rigid!(A::AbstractAtomContainer{T}, B::AbstractAtomContainer{T})
map_rigid!(A::AtomTable{T}, B::AtomTable{T})
```

与えられた原子の双射に対して、RMSDを最小化する剛体変換を計算し、適用し、返します。引数が原子コンテナまたはテーブルの場合、デフォルトで[`TrivialAtomBijection`](@ref)が使用されます。最初の構造（`A`）のみが変更され、2番目の構造（`B`）にマッピングされます。

# サポートされているキーワード引数

  * `heavy_atoms_only::Bool = false` `true`の場合、最適な変換の計算中に水素原子は無視されます。そうでない場合、すべての原子が使用されます。
  * `minimizer::Type{<: AbstractRMSDMinimizer} = RMSDMinimizerCoutsias` [`compute_rmsd_minimizer`](@ref)を参照してください。
