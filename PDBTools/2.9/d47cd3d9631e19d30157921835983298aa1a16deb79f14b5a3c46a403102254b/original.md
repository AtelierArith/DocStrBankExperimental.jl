```
remove_custom_elements!()
```

Remove all custom elements from the elements dictionary.

# Example

```jldoctest
julia> using PDBTools

julia> remove_custom_elements!();

julia> add_element!("GN", PDBTools.elements["N"])
PDBTools.Element(:N, "N", "Nitrogen", 7, 14.0067, true)

julia> element(Atom(name="GN"))
"N"

julia> remove_custom_elements!();

julia> element(Atom(name="GN")) # returns `nothing`

```

Here we repeteadly call `remove_custom_elements!()` to guarantee the proper execution of the test codes, without any custom elements predefined.
