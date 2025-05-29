```julia
covalent_radius(atom::Chemfiles.Atom) -> Float64

```

Get the covalent radius of an `atom` from the atom type.

If the radius can not be found, returns 0.
