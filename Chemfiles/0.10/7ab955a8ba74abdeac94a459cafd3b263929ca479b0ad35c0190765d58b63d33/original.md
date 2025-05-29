```julia
atomic_number(atom::Chemfiles.Atom) -> UInt64

```

Get the atomic number of an `atom` from the atom type.

If the atomic number can not be found, returns 0.
