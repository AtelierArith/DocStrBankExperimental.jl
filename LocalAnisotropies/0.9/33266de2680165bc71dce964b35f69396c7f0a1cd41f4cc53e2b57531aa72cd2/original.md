```
localanisotropies(data, rotation, ranges, convention=nothing)
localanisotropies(data, ranges, convention) # assumes angles [:ang1,:ang2,:ang3]
localanisotropies(data, ranges) # assumes quaternions [:q0,:q1,:q2,:q3]
```

Import a `LocalAnisotropy` object from tabular data. The `data` must follow `Tables.jl` structure. It must have the rotation info and ranges as properties. These property names are informed as vectors in `rotation` and `ranges`for the conversion. Check out the available rotation conventions at [`RotationRule`](@ref) docstring.

## Example

```julia
localanisotropies(data, [:rot1], [:range1, :range2], :EulerIntr) # 2D
localanisotropies(data, [:rot1, :rot2, :rot3], [:range1, :range2, :range3], :GSLIB) # 3D
localanisotropies(data, [:q0,:q1,:q2,:q3], [:range1, :range2, :range3]) # quaternion
```
