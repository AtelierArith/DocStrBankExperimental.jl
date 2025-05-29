each*ell*m(alm::Alm{Complex{T}}) where {T <: Number} -> Vector{Int}

```
Returns an array of tuples `(l, m)` of all the ℓ and m values of `alm` in
m-major order (the same order as how the harmonic coefficients are stored in `Alm` objects).
```
