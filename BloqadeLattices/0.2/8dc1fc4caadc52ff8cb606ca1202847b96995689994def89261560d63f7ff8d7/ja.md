```
two_body_interaction_matrix(f, atoms)
```

2つの原子位置を受け取る関数 `f` と、原子位置を含むインデックス可能な反復可能オブジェクト `atoms` を与えると、相互作用行列を生成します。

関連情報は [`rydberg_interaction_matrix`](@ref) を参照してください。

```jldoctest; setup=:(using BloqadeLattices)
julia> atoms = [(0.0,), (1.0,), (2.0,), (3.0,)]; # 1Dチェーン、AtomListとしても使用可能

julia> two_body_interaction_matrix(atoms) do x,y return 1/distance(x,y) end
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 0.0  1.0  0.5  0.333333
  ⋅   0.0  1.0  0.5
  ⋅    ⋅   0.0  1.0
  ⋅    ⋅    ⋅   0.0
```
