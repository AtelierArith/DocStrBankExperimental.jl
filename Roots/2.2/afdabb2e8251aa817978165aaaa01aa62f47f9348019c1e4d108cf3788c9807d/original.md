```
Order16()
Thukral16()
```

Implements the order 16 algorithm from *New Sixteenth-Order Derivative-Free Methods for Solving Nonlinear Equations* by R. Thukral, American Journal of Computational and Applied Mathematics p-ISSN: 2165-8935;    e-ISSN: 2165-8943; 2012;  2(3): 112-118 DOI: [10.5923/j.ajcam.20120203.08](https://doi.org/10.5923/j.ajcam.20120203.08).

Five function calls per step are required. Though rapidly converging, this method generally isn't faster (fewer function calls/steps) over other methods when using `Float64` values, but may be useful for solving over `BigFloat`.  The `Order16` method replaces a Steffensen step with a secant step when `f(x)` is large.

The error, `eᵢ = xᵢ - α`, is expressed as `eᵢ₊₁ = K⋅eᵢ¹⁶` for an explicit `K` in equation (50) of the paper.
