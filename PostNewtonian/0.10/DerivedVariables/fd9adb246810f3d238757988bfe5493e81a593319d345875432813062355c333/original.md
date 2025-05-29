```
Ω(pnsystem)
Ω(;v, M=1)
Omega(pnsystem)
Omega(;v, M=1)
```

Orbital angular frequency.

The parameter `v` is the PN velocity parameter, and must be passed as a keyword argument — as in `Ω(v=0.1)`.  The parameter `M` is the total mass of the binary.  They are related *by definition* as

$$
\Omega \colonequals \frac{v^3}{M}.
$$

See also [`v`](@ref).
