```
li5(z::Complex)
```

Returns the complex 5th order polylogarithm $\operatorname{Li}_5(z)$ of a complex number $z$ of type `ComplexF`.

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> li5(1.0 + 1.0im)
0.9874666591701127 + 1.068441607107422im
```
