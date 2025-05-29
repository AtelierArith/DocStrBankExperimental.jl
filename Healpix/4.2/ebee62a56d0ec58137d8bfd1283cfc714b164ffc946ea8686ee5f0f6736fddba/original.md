dot(alm₁::Alm{Complex{T}}, alm₂::Alm{Complex{T}}) where {T <: Number}

```
Implements the dot product in a_ℓm space.
The two imput alms must have matching size, lmax and mmax.
A new `Alm` object is returned.
```
