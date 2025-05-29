```
DataDomain(domain::JutulDomain; property1 = p1, property2 = p2, ...)
```

A wrapper around a domain that allows for storing of entity-associated data.

Example:

```julia
# Grid with 6 cells and 7 interior faces
g = CartesianMesh((2, 3))
d = DataDomain(g)
d[:cell_vec] = rand(6) #ok, same as:
d[:cell_vec, Cells()] = rand(6) #ok
d[:cell_vec, Faces()] = rand(6) #not ok!
d[:face_vec, Faces()] = rand(7) #ok!
# Can also add general arrays if last dimension == entity dimension
d[:cell_vec, Cells()] = rand(10, 3, 6) #ok
# Can add general data too, but needs to be specified
d[:not_on_face_or_cell, nothing] = rand(3) # also ok
```
