```
BoundedLattice(lattice::AbstractLattice{D},region::AbstractRegion{D},pbc::Bool=false)
```

与えられた基盤の `lattice` と格子上の境界となる `region` を使用して [`BoundedLattice`](@ref) インスタンスを作成し、周期境界条件を有効にするオプションがあります。

関連情報: [`parallelepiped_region`](@ref)
