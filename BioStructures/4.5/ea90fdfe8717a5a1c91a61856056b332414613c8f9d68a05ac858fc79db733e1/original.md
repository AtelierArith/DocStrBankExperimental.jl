```
ContactMap(element, contact_distance)
ContactMap(element_one, element_two, contact_distance)
ContactMap(bit_array_2D)
```

Calculate the contact map for a `StructuralElementOrList`, or between two `StructuralElementOrList`s.

This returns a `ContactMap` type containing a `BitArray{2}` with `true` where the sub-elements are no further than the contact distance and `false` otherwise. When one element is given as input this returns a symmetric square matrix. To directly access the underlying data of `ContactMap` `cm`, use `cm.data`.

# Examples

```julia
cbetas_A = collectatoms(struc["A"], cbetaselector)
cbetas_B = collectatoms(struc["B"], cbetaselector)

# Contact map of chain A using conventional Cβ and 8 Å definitions
cm = ContactMap(cbetas_A, 8.0)

# Returns true if a contact is present between the tenth and twentieth element
cm[10, 20]

# Rectangular contact map of chains A and B
cm = ContactMap(cbetas_A, cbetas_B, 8.0)

# Write the contact map to file
using DelimitedFiles
writedlm("contacts.out", Int64.(cm.data), " ")
```
