```
castDef(grid::CamiDiff.Grid{T}, atom::Atom, spinorbit::Spinorbit, codata::Codata [; pos=nothing, [scr=nothing[, msg=false]]) where T <: Real
```

Create the [`Def`](@ref) object starting from the [`CamiDiff.Grid`](@extref) object and the atomic properties of the objects [`Atom`](@ref) and [`Orbit`](@ref). Optional: scr (supply screening array)

#### Example:

```
julia> codata = castCodata(2018)
julia> atom = castAtom(Z=1, A=1, Q=0);
julia> orbit = castOrbit(n=7, ℓ=2);
julia> grid = autoGrid(atom, orbit, Float64);

julia> castDef(grid, atom, orbit, codata, msg=true);
Def created for hydrogen 7d on exponential grid of 400 points
```
