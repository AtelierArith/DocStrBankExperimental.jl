```
autoPrecision(rmax::T, ℓ = 0) where T<:Real
```

浮動小数点精度（経験則値）

### 例：

```
julia> atom = castAtom(Z=1);

julia> orbit = castOrbit(n=1,ℓ=0);

julia> rmax = autoRmax(atom, 0; rmax=0.0); println("rmax = $(rmax) a.u.")
rmax = 77.5 a.u.

julia> o = autoPrecision(rmax, 0); println("precision = $o")
precision = Float64
```
