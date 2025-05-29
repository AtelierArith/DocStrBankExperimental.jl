```
load_gmsh_file(filename::AbstractString) -> NamedTuple
```

Loads `filename` into separete arrays according to the gmsh file format style in ASCII mode.

# Arguments

  * `filename::AbstractString`: name of the file to be loaded,

# Keywords

# Returns

  * `NamedTuple`: gmsh file is separated into the arrays of substring:

      * msh_version - constains infomartion about gmsh file version,
      * msh_PhysicalNames - constains data about physical objects,
      * msh_Entities - constains data about entities,
      * msh_Nodes - constains data about nodes including coordinates,
      * msh_Elements - constains data about elements,

# Throws

  * `Error`: file with name `filename` does not exists,
  * `Error`: file with name `filename` is saved in binary mode.
