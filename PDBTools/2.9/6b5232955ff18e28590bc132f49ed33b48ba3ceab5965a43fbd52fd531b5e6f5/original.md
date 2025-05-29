```
element_symbol_string(atom::Atom)
```

Returns a string with the symbol of the element, given the `Atom` structure.

### Example

```jldoctest
julia> using PDBTools 

julia> at = Atom(name="NT3");

julia> element_symbol_string(at)
"N"
```
