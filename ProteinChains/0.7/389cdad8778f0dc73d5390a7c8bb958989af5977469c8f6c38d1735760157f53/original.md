```
append_residue(Backbone::Backbone, torsion_angles::Vector{<:Real}; ideal::BackboneGeometry=DEFAULT_BACKBONE_GEOMETRY)
```

Create a new backbone by prepending 3 new torsion angles (ψ, ω, ϕ) at the beginning, using bond lengths and bond angles specified in the `BackboneGeometry`.

!!! note
    The torsion angle order is the same as it would be when appending. The order is *not* reversed.

