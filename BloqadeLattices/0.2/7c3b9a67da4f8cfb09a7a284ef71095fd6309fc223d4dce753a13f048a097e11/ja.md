```
lattice_sites(lattice::BoundedLattice{L,C})
```

`BoundedLattice`の単位セルを定義する基礎となるサイトベクトルを返します。

```jldoctest; setup=:(using BloqadeLattices)
julia> bl = parallelepiped_region(SquareLattice(),(3,0),(0,2);) # 2D BoundedLatticeを作成

julia> lattice_sites(bl) # 基礎となるSquareLatticeのブラヴェ格子定義に使用される格子ベクトル
((0.0, 0.0), )
```
