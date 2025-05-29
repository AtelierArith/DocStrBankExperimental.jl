# Riemann Liouville sense fractional integral using cubic spline interpolation to approximate.

### Example

```julia-repl
julia> fracint(x->x, 0.5, 1, 0.0001, RLIntCubicSplineInterp())
0.7529119186452693
```

Error estimate of this method is $\mathcal{O(h^4)}$, it is determined by the error of the cubic spline interpolation.

!!! warning "Set h as 0.001 or bigger"
    For some reason, in the **RLIntCubicSplineInterp** method, set **h** as 0.001 would get better result.


> Numerical Methods for Fractional Calculus Page 34

