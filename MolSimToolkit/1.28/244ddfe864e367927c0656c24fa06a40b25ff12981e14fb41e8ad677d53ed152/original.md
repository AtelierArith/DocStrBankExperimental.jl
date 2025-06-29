```
FramePositions{T,P<:Point3D{T},M<:AbstractArray{T}} <: AbstractVector{P}
```

Container for the positions of a set of atoms. The positions are stored in a matrix, where each column corresponds to the coordinates of an atom. The container is used such that using the coodinates from a `Chemfiles.Frame` is transparent to the user, and the coordinates can be accessed as `p[i]` where `i` is the index of the atom. 

The coordinates of the atom can be accessed as `p[i].x`, `p[i].y`, and `p[i].z`.

A `FramePositions` object can be created with the `positions` function. The construction with `FramePositions` is not considered part of the public API.

# Example

```julia-repl # to be doctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> frame = current_frame(simulation);

julia> p = positions(frame)
20465-element FramePositions{Float64, Point3D{Float64}, Chemfiles.ChemfilesArray}:
 [5.912472724914551, 10.768872261047363, 28.277008056640625]
 [5.040304183959961, 10.810898780822754, 27.71207046508789]
 ⋮
 [11.16289234161377, -37.30374526977539, 22.80788230895996]

julia> p[1]
3-element Point3D{Float64} with indices SOneTo(3):
  5.912472724914551
 10.768872261047363
 28.277008056640625

julia> p[1].x
5.912472724914551

julia> p[1].y
10.768872261047363

julia> p[1].z
28.277008056640625
```

It is also possible to take slices and views of the positions:

```
julia> p[1:2]
2-element FramePositions{Float64, Point3D{Float64}, Matrix{Float64}}:
 [5.912472724914551, 10.768872261047363, 28.277008056640625]
 [5.040304183959961, 10.810898780822754, 27.71207046508789]

julia> @view(coor[1:2])
 2-element FramePositions{Float64, Point3D{Float64}, SubArray{Float64, 2, Chemfiles.ChemfilesArray, Tuple{Base.Slice{Base.OneTo{Int64}}, UnitRange{Int64}}, false}}:
  [5.912472724914551, 10.768872261047363, 28.277008056640625]
  [5.040304183959961, 10.810898780822754, 27.71207046508789]
 
```
