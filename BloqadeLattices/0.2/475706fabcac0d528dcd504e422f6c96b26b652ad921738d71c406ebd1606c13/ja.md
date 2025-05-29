```
parallelepiped_region(lattice::AbstractLattice{D},M::Vararg{NTuple{D,Int},D};pbc::Bool=false;scale::Real=1)
```

既存の格子と、格子ベクトルの整数倍で定義された平行四辺形/平行六面体/線分を定義するタプルを使用して `BoundedLattice` を作成します。

周期境界条件は `pbc` を介して有効化/無効化できます。タプルは格子引数の次元と同じ長さと数量でなければなりません。

```jldoctest; setup=:(using BloqadeLattices)
julia> parallelepiped_region(SquareLattice(),(2,0),(0,2);pbc=true);

julia> parallelepiped_region(KagomeLattice(),(2,2),(-2,2));
```
