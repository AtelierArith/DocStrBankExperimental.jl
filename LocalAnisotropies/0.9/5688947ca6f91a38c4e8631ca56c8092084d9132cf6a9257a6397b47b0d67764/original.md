```
convertangles(angles, convention1, convention2) # angles to new angles
convertangles(angles, convention1) # angles to quaternion
```

Convert angles between different convention. Check out the available rotation conventions at [`RotationRule`](@ref) docstring.

## Example

Converting 3D rotation [30, 30 30] from GSLIB convention to Datamine convention

```julia
new_angs = convertangles([30,30,30], :GSLIB, :Datamine)
```
