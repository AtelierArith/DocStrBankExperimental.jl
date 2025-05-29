Returns a mesh on the same vertexbuffer as the input mesh. The submesh will be a mesh of dimension k containing all the k-cells that are in mesh and that fulfill the predicate pred.

`pred` is a function with signature `pred(cell) -> Bool` returning true if the simplex is to be added to the submesh under construction.
