```
add_element!(symbol::String, reference_element::PDBTools.Element; elements=PDBTools.elements)
```

Add a new element to the elements dictionary. If the element already exists, overwrite it.

To remove all custom elements, use `remove_custom_elements!()`.

# Example

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> using PDBTools

julia> remove_custom_elements!(); # if any

julia> atoms = [ Atom(name="A1"), Atom(name="A2") ];

julia> add_element!("A1", PDBTools.elements["C"])
PDBTools.Element(:C, "C", "Carbon", 6, 12.011, true)

julia> add_element!("A2", PDBTools.elements["N"])
PDBTools.Element(:N, "N", "Nitrogen", 7, 14.0067, true)

julia> element(atoms[1])
"C"

julia> element(atoms[2])
"N"

julia> mass(atoms)
26.017699999999998

julia> remove_custom_elements!(); 
```

Here we repeteadly call `remove_custom_elements!()` to guarantee the proper execution of the test codes, without any custom elements predefined.
