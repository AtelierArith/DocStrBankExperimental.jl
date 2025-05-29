```
element_name(atom::Atom)
```

Returns the element name of an atom given its name, or `Atom` structure.

### Example

```jldoctest
julia> using PDBTools

julia> at = Atom(name="NT3");

julia> element_name(at)
"Nitrogen"
```
