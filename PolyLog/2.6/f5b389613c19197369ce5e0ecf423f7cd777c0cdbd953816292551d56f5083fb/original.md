```
li6(z::Complex)
```

Returns the complex 6th order polylogarithm $\operatorname{Li}_6(z)$ of a complex number $z$ of type `Complex`.

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> li6(1.0 + 1.0im)
0.996149796835317 + 1.0335544477237482im
```
