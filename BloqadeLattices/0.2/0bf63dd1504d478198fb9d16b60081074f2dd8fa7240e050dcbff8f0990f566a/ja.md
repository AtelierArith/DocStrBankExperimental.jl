```
rydberg_interaction_matrix(atoms, C::Real)
rydberg_interaction_matrix(lattice::BoundedLattice{L,R},C::Real)
```

インデックス可能な反復可能な `atoms` を与えられた位置の原子と、リュードベリ相互作用定数 `C` に基づいて相互作用行列を生成します。

`atoms` の代わりに `BoundedLattice` を使用することができ、周期境界条件を考慮した格子のリュードベリ相互作用行列を生成します。

詳細は [`two_body_interaction_matrix`](@ref) を参照してください。

```jldoctest; setup=:(using BloqadeLattices)
julia> atoms = [(0.0,), (1.0,), (2.0,), (3.0,)]; # 原子の1Dチェーン

julia> rydberg_interaction_matrix(atoms, 2π * 862690) # リュードベリ定数を提供
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 0.0  5.42044e6  84694.4         7435.45
  ⋅   0.0            5.42044e6  84694.4
  ⋅    ⋅             0.0            5.42044e6
  ⋅    ⋅              ⋅             0.0

julia> bl = parallelepiped_region(SquareLattice(),(2,0),(0,2);pbc=true); 

julia> rydberg_interaction_matrix(bl, 2π * 862690)
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 0.0  5.42044e6  5.42044e6  6.77555e5
  ⋅   0.0        6.77555e5  5.42044e6
  ⋅    ⋅         0.0        5.42044e6
  ⋅    ⋅          ⋅         0.0
```
