```
cl5(x::Real)::Real
```

Returns the value of the Clausen function $\operatorname{Cl}_5(x)$ for a real angle $x$ of type `Real`.  This function is defined as

$$
\operatorname{Cl}_5(x) = \Re[\operatorname{Li}_5(e^{ix})] = \sum_{k=1}^\infty \frac{\cos(kx)}{k^5}
$$

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl5(1.0)
0.5228208076420943
```
