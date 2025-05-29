```
lattice_vectors(lattice::BoundedLattice{L,C})
```

`BoundedLattice`の基になるブラヴァ格子ベクトルを返します。

```jldoctest; setup=:(using BloqadeLattices)
julia> bl = parallelepiped_region(SquareLattice(),(3,0),(0,2);) # 2D BoundedLatticeを作成

julia> lattice_vectors(bl) # 基になるSquareLatticeのブラヴァ格子定義に使用される格子ベクトル
((1.0, 0.0), (0.0, 1.0))
```
