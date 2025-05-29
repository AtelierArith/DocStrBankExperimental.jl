```
state(s::Index, name::String; kwargs...)
```

Return an ITensor corresponding to the state named `name` for the Index `s`. The returned ITensor will have `s` as its only index.

The terminology here is based on the idea of a single-site state or wavefunction in physics.

The `state` function is implemented for various Index tags by overloading either the `state` or `state!` methods which take a `SiteType` argument corresponding to one of the tags of the Index `s` and an `StateName"name"` argument that corresponds to the input state name.

The `state` system is used by the MPS type to construct product-state MPS and for other purposes.

# Example

```julia
s = Index(2, "Site,S=1/2")
sup = state(s,"Up")
sdn = state(s,"Dn")
sxp = state(s,"X+")
sxm = state(s,"X-")
```
