```
struct BoundedLattice{L<:AbstractLattice, R<:AbstractRegion}
```

領域によって制約された格子を定義し、周期境界条件のオプションを提供します。

# フィールド

  * `lattice <: AbstractLattice`: 制約される格子。
  * `region <: AbstractRegion`: 基本となる `lattice` を制約する領域。
  * `site_positions::AtomList`: `region` 内の原子の位置。
  * `pbc::Bool`: 周期境界条件の動作を有効/無効にします。
