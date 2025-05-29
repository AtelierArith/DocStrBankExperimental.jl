```julia
imsci(A::AbstractArray, colormap::AbstractVector=viridis, cmin=nanminimum(A), cmax=nanmaximum(A))
```

Convert a matrix `A` to an indirect array image (an IndirectArray of Colors.jl colors) using the specified `colormap` (default `viridis`), optionally scaled between `cmin` and `cmax`.

As `imsc`, but returns an IndirectArray; slightly more space efficient for small colormaps, but with computational cost.

### Examples

```julia
julia> A = rand(3,3)
3×3 Matrix{Float64}:
 0.39147   0.553489  0.351628
 0.331786  0.343836  0.824674
 0.639233  0.558113  0.965627

 julia> img = imsci(A)
 3×3 IndirectArrays.IndirectArray{RGB{N0f8}, 2, UInt64, Matrix{UInt64}, Vector{RGB{N0f8}}}:
  RGB{N0f8}(0.282,0.137,0.455)  …  RGB{N0f8}(0.278,0.051,0.376)
  RGB{N0f8}(0.267,0.004,0.329)     RGB{N0f8}(0.431,0.808,0.345)
  RGB{N0f8}(0.133,0.553,0.553)     RGB{N0f8}(0.992,0.906,0.145)

julia> using Images; save("img.png", img) # Save to file as PNG

julia> using Plots; plot(0:3, 0:3, img) # Plot with specified x and y axes
```
