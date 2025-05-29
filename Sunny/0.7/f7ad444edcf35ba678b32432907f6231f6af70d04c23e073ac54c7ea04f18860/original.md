```
domain_average(f, cryst, qpts; rotations, weights)
```

Calculate an average intensity for the reciprocal-space points `qpts` under a discrete set of `rotations`. Rotations, in global coordinates, may be given either as an axis-angle pair or as a 3×3 rotation matrix. Each rotation is weighted according to the elements in `weights`. The function `f` should accept a list of rotated q-points and return an [`intensities`](@ref) calculation.

# Example

```julia
# 0, 120, and 240 degree rotations about the global z-axis
rotations = [([0,0,1], n*(2π/3)) for n in 0:2]
weights = [1, 1, 1]
res = domain_average(cryst, path; rotations, weights) do path_rotated
    intensities(swt, path_rotated; energies, kernel)
end
plot_intensities(res)
```
