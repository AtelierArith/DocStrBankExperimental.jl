Check whether a given gate is in (a specific region of) the Weyl chamber.

```
in_weyl_chamber(c₁, c₂, c₃)
```

checks whether `c₁`, `c₂`, `c₃` are valid Weyl chamber coordinates.

```
in_weyl_chamber(U; region="PE")
in_weyl_chamber(c₁, c₂, c₃; region="PE")
```

checks whether the two-qubit gate `U`, respectively the gate described by the Weyl chamber coordinates `c₁`, `c₂`, `c₃` (see [`weyl_chamber_coordinates`](@ref)) is a perfect entangler. The `region` can be any other of the regions returned by [`weyl_chamber_region`](@ref).
