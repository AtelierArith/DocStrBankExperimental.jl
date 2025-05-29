```
fracdiff(f, α, point, h, FracDiffAlg())
```

`fracdiff` is the general function for computing fractional derivative.

### Example

```julia-repl
julia> fracdiff(x->x^2, 0.5, 1, 0.001, RLDiffL1())
1.5044908143658473
```

There are many algorithms can be used to computing fractional derivative, please refer to our manual for more details: http://scifracx.org/FractionalCalculus.jl/dev/Derivative/derivativeapi/.
