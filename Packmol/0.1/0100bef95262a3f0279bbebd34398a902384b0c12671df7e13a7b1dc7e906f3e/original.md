```
pack_monoatomic!(positions::AbstractVector{<:SVector{N,T}}, unitcell, tol)
```

Pack a monoatomic system with iniital positions `x` and distance tolerance `tol`, into the unitcell defined by `unitcell`, considering periodic boundary conditions.

The unitcell can be a vector, in the case of orthorhombic cells, or a matrix, in the case of triclinic cells.

The coordinates and the unitcells can be two- or three-dimensional. 

# Example

```julia-repl
julia> using Packmol, StaticArrays

julia> coordinates = 100 * rand(SVector{3,Float64}, 10^5);

julia> unitcell = [100.0, 100.0, 100.0]; tolerance = 2.0;

julia> pack_monoatomic!(coordinates, unitcell, tolerance)
```

After packing, the `coordinates` array will have updated positions for the atoms without overlaps. 
