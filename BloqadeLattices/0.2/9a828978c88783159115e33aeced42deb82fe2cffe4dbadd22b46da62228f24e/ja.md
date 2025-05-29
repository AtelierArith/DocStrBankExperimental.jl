```
dimension(lattice::BoundedLattice{L,C})
```

`BoundedLattice`の次元を返します（例：2Dの場合は`2`、3Dの場合は`3`）

```jldoctest; setup=:(using BloqadeLattices)
julia> bl = parallelepiped_region(ChainLattice(),(4,);pbc=true) # 1D BoundedLatticeを作成

julia> dimension(bl)
1

julia> bl = parallelepiped_region(SquareLattice(),(3,0),(0,2);) # 2D BoundedLatticeを作成

julia> dimension(bl)
2
```
