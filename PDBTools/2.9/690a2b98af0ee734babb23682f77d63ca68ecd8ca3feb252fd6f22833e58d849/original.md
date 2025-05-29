```
atomic_number(atom::Atom)
```

Returns the atomic number of an atom from its `Atom` structure.

### Example

```jldoctest
julia> using PDBTools

julia> at = Atom(name="NT3");

julia> atomic_number(at)
7
```
