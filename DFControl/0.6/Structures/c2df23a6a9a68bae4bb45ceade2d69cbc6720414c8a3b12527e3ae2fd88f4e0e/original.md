```
Atom(name::Symbol, element::Element, position_cart::Point3{Length}, position_cryst::Point3;
     pseudo::String = "",
     projections::Vector{Projection} = Projection[],
     magnetization::Vec3 = Vec3(0.0, 0.0, 0.0),
     dftu::DFTU = DFTU())
```

Representation of an `atom`.

The `name` of the `atom` is used as an identifier for the `atom` type, in the sense that atoms with the same `pseudo`, `projections`, `magnetization` and [`dftu`](@ref DFTU) attributes should belong to the same type. This also means that during sanity checks atoms that are not of the same type will be given different names. This is done in this way because it often makes sense to change these parameters on all atoms of the same kind at the same time, but still allow the flexibility to change them for individual atoms as well.

`position_cart` should have a valid `Unitful.Length` type such as `Ang`.

See documentation for [`Element`](@ref) for further information on this attribute.
