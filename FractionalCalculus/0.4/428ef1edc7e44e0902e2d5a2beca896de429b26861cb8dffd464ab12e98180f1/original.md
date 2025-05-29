```
fracint(f, α, point, h, FracIntAlg())
```

The general function used for fractional integral computing.

### Example

```julia-repl
julia> fracint(x->x^2, 0.5, 1, 0.001, RLInt_Approx())
0.6017877646029814
```

There are many algorithms can be used to computing fractional integral, please refer to our manual for more details: [manual](http://scifracx.org/FractionalCalculus.jl/dev/Integral/integralapi/).
