zplot(f, z; coloring=artist()) zplot(f, xlims=[-4, 4], ylims=[-4, 4], n=800; coloring=artist()) Plot a complex-valued function `f` evaluated over the points in matrix `z`, or on an `n`×`n` grid over `xlims`×`ylims` in the complex plane. The method for coloring values is given by the keyword argument `coloring`.

zplot(z; coloring=artist()) Plot a matrix of complex values coloring according to the function given by the keyword argument `coloring`. It is presumed that `z` results from evaluation on a grid in the complex plane.

# Examples

```julia
zplot(z -> (z^3 - 1) / sin(2im - z))
zplot(tanh)
zplot(tanh, coloring=artist(1.5))  # to see more magnitude contours
```
