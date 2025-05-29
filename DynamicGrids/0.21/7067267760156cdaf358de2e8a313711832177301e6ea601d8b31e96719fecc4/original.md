```
Convolution <: NeighborhoodRule

Convolution(kernel::AbstractArray)
Convolution{R,W}(kernel::AbstractArray)
```

A [`NeighborhoodRule`](@ref) that runs a convolution kernel over the grid.

`kernel` must be a square matrix.

## Performance

Small radius convolutions in DynamicGrids.jl will be comparable or even faster than using DSP.jl or ImageConvolutions.jl. As the radius increases these packages will be a lot faster.

But `Convolution` is convenient to chain into a simulation, and combined with some other rules. It should perform reasonably well with all but very large kernels.

Values are not normalised, so make sure the kernel sums to `1` if you need that.

## Example

A streaking convolution that looks a bit like sand blowing.

Swap out the matrix values to change the pattern.

```julia
using DynamicGrids, DynamicGridsGtk
streak = Convolution([0.0 0.01 0.48; 
                      0.0 0.5  0.01; 
                      0.0 0.0  0.0])
output = GtkOutput(rand(500, 500); tspan = 1:1000, fps=100)
sim!(output, streak; boundary=Wrap())
```
