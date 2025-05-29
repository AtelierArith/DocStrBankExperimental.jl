```
cl4(x::Real)::Real
```

Returns the value of the Clausen function $\operatorname{Cl}_4(x)$ for a real angle $x$ of type `Real`.  This function is defined as

$$
\operatorname{Cl}_4(x) = \Im[\operatorname{Li}_4(e^{ix})] = \sum_{k=1}^\infty \frac{\sin(kx)}{k^4}
$$

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl4(1.0)
0.8958052386793799
```
