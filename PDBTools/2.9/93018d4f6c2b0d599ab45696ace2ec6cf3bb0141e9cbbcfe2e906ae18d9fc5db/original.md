```
element(atom::Atom)
```

Returns the element symbol, as a string, of an atom given the `Atom` structure. If the `pdb_element` is empty or "X", the element is inferred from the atom name.  Othwerwise, the `pdb_element` is returned.

### Example

```jldoctest
julia> using PDBTools

julia> at = Atom(name="NT3");

julia> element(at)
"N"
```
