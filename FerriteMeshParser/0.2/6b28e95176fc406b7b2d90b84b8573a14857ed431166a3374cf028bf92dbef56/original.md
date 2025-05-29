```
function get_ferrite_grid(
    filename; 
    meshformat=AutomaticMeshFormat(), 
    user_elements=Dict{String,DataType}(), 
    generate_facetsets=true
    )
```

Create a `Ferrite.Grid` by reading in the file specified by `filename`.

Optional arguments:

  * `meshformat`: Which format the mesh    is given in, normally automatically detected by the file extension
  * `user_elements`: Used to add extra elements not supported,   might require a separate cell constructor.
  * `generate_facetsets`: Should facesets be automatically generated from all nodesets?
