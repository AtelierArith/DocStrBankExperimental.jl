```
coor(atoms; selection)
```

原子の座標を返します。入力は1つの原子（`Atom`型）、原子のベクトル、または`Residue`である可能性があります。座標は静的ベクトル（`StaticArrays`から）として、より具体的には`Vector{SVector{3,Float64}}`として返されます。

### 例

```julia-repl
julia> using PDBTools, StaticArrays 

julia> protein = wget("1LBD");

julia> coor(protein[1])
3-element SVector{3, Float64} with indices SOneTo(3):
 45.228
 84.358
 70.638

julia> coor(protein[1],as=SVector{3,Float32})
3-element SVector{3, Float32} with indices SOneTo(3):
 45.228
 84.358
 70.638

julia> coor(protein, "index <= 2")
2-element Vector{SVector{3, Float64}}:
 [45.228, 84.358, 70.638]
 [46.08, 83.165, 70.327]

julia> coor(protein, only = at -> at.resname == "ALA")
110-element Vector{SVector{3, Float64}}:
 [43.94, 81.982, 70.474]
 [43.02, 80.825, 70.455]
 [41.996, 80.878, 69.34]
 ⋮
 [-17.866, 84.088, 51.741]
 [-18.496, 83.942, 52.777]
 [-15.888, 82.583, 51.706]
  
julia> residues = collect(eachresidue(protein));

julia> coor(residues[1])
6-element Vector{SVector{3, Float64}}:
 [45.228, 84.358, 70.638]
 [46.08, 83.165, 70.327]
 [45.257, 81.872, 70.236]
 [45.823, 80.796, 69.974]
 [47.147, 82.98, 71.413]
 [46.541, 82.639, 72.662]

```
