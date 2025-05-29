```
cl6(x::Real)::Real
```

Returns the value of the Clausen function $\operatorname{Cl}_6(x)$ for a real angle $x$ of type `Real`.  This function is defined as

$$
\operatorname{Cl}_6(x) = \Im[\operatorname{Li}_6(e^{ix})] = \sum_{k=1}^\infty \frac{\sin(kx)}{k^6}
$$

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl6(1.0)
0.855629273183937
```
