```
Order8()
Thukral8()
```

Implements an eighth-order algorithm from *New Eighth-Order Derivative-Free Methods for Solving Nonlinear Equations* by Rajinder Thukral, International Journal of Mathematics and Mathematical Sciences Volume 2012 (2012), Article ID 493456, 12 pages DOI: [10.1155/2012/493456](https://doi.org/10.1155/2012/493456). Four function calls per step are required.  The `Order8` method replaces a Steffensen step with a secant step when `f(x)` is large.

The error, `eᵢ = xᵢ - α`, is expressed as `eᵢ₊₁ = K ⋅ eᵢ⁸` in (2.25) of the paper for an explicit `K`.
