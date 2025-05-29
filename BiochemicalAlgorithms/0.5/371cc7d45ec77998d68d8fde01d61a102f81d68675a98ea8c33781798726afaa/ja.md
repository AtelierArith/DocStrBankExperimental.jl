```
compute_rmsd(f::AbstractAtomBijection)
compute_rmsd(A::AbstractAtomContainer{T}, B::AbstractAtomContainer{T})
compute_rmsd(A::AtomTable{T}, B::AtomTable{T})
```

与えられた原子の対応の[二乗平均平方根偏差 (RMSD)](https://en.wikipedia.org/wiki/Root-mean-square_deviation_of_atomic_positions)を計算します。引数が原子コンテナまたはテーブルの場合は、デフォルトで[`TrivialAtomBijection`](@ref)が使用されます。
