```julia
vdw_radius(atom::Chemfiles.Atom) -> Float64

```

Get the van der Waals radius of an `atom` from the atom type.

If the radius can not be found, this function returns 0.
