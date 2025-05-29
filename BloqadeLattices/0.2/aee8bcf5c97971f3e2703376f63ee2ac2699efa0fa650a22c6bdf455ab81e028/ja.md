```
distance(lattice::BoundedLattice,x,y)
```

[`BoundedLattice`](@ref)内の2点間の距離を返します。

点`x`と`y`は任意の反復可能なものであり、[`BoundedLattice`](@ref)と同じ次元を持つ必要があります（例：2D格子の場合は`(x,y)`、3D格子の場合は`(x,y,z)`）。

[`BoundedLattice`](@ref)に対して周期境界条件オプションが`true`に設定されている場合、点間の最小距離（領域の剰余）が返されます。それ以外の場合は、標準のユークリッド距離が使用されます。

```jldoctest; setup=:(using BloqadeLattices)
julia> bl = parallelepiped_region(SquareLattice(), (1,0),(0,1);) # 2D BoundedLatticeを定義

julia> distance(bl, (0.1, 0.1), (0.5, 1.1)) # 2点間の距離
1.077032961426901

julia> bl_pbc = parallelepiped_region(SquareLattice(), (1,0),(0,1);pbc=true) # 周期境界条件付きの2D BoundedLatticeを定義

julia> distance(bl_pbc, (0.1, 0.1), (0.5, 1.1)) # 周期境界条件が有効な距離
0.4
```
