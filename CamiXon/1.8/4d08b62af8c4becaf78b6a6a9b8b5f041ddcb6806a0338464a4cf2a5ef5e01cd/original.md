```
autoPrecision(rmax::T, ℓ = 0) where T<:Real
```

Floating point precision (rule of thumb value)

### Example:

```
julia> atom = castAtom(Z=1);

julia> orbit = castOrbit(n=1,ℓ=0);

julia> rmax = autoRmax(atom, 0; rmax=0.0); println("rmax = $(rmax) a.u.")
rmax = 77.5 a.u.

julia> o = autoPrecision(rmax, 0); println("precision = $o")
precision = Float64
```
