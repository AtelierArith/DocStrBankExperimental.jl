```julia
struct LeastSquares <: VIDA.AbstractDivergence
```

Type for the least squares divergence. It constructed from an `IntensityMap` i.e. data. Additionally to evaluate the divergence we use a functor approach where if θ is your

### Details

This computes the squared 2 norm between your image and template, both of which are normalized to unit flux.

To construct this just pass it an image object

```julia-repl
julia> ls = LeastSquares(img::IntensityMap)
```

# Notes

We have a template internal matrix the prevents internal allocations during computation This is a internal feature that the user does not need to worry about.
