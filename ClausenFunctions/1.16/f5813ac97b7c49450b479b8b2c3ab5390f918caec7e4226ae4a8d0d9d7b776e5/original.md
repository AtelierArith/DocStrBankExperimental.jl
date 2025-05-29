```
cl2(x::Real)::Real
```

Returns the value of the Clausen function $\operatorname{Cl}_2(x)$ for a real angle $x$ of type `Real`.  The Clausen function is defined as

$$
\operatorname{Cl}_2(x) = -\int_0^x \log|2\sin(t/2)| dt
$$

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl2(1.0)
1.0139591323607684
```
