```
append_residue(Backbone::Backbone, torsion_angles::Vector{<:Real}; ideal::BackboneGeometry=DEFAULT_BACKBONE_GEOMETRY)
```

Create a new backbone by appending 3 new torsion angles (ψ, ω, ϕ) at the end, using bond lengths and bond angles specified in `BackboneGeometry`.
