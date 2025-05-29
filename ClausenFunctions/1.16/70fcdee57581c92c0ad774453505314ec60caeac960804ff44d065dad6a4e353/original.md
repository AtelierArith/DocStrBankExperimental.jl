```
cl3(x::Real)::Real
```

Returns the value of the Clausen function $\operatorname{Cl}_3(x)$ for a real angle $x$ of type `Real`.  This function is defined as

$$
\operatorname{Cl}_3(x) = \Re[\operatorname{Li}_3(e^{ix})] = \sum_{k=1}^\infty \frac{\cos(kx)}{k^3}
$$

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl3(1.0)
0.44857300728001737
```
