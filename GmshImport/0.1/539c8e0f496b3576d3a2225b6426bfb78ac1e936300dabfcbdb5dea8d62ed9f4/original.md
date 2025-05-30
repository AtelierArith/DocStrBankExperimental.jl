```
gmsh_import(filename,
    process_elementtypes = String[],
    add_elementtypes = Dict()
    )
```

Import GMSH finite element mesh file.

# Optional arguments

  * `process_elementtypes`: array of names of the element type derived from the definitions in `https://gitlab.onelab.info/gmsh/gmsh/blob/master/src/common/GmshDefines.h`. To derive the name of the element type, take as an example `#define MSH_QUA_4 3`. Strip off `MSH_`, and replace the underscore with a space: "QUA 4". If the array `process_elementtypes` is empty (which is the default), the assumption is that all element types should be processed. Example: `["LIN 2", ]` requests that only line elements with two nodes should be processed.
  * `add_elementtypes`: dictionary of additional element type definitions. Refer to `https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format`. The dictionary is indexed by the name of the element type (a string), and the value is a tuple of the element type integer, and the number of nodes per element. Example: Passing `Dict("TRI 15" => (23, 15),)` will add the type of triangles with 15 nodes. The current defaults are `GmshImport.elementtypes_definitions`.

# Returns

  * `nodeblocks`: Node blocks is an array of named tuples, each with the data:

      * `block` = block id,
      * `entdim` = entity dimension,
      * `enttag` = entity tag,
      * `parcoor` = parametric coordinates supplied?,
      * `nnodes` = number of nodes located on this entity,
      * `ntags` = array of node tags,
      * `ncoor` = array of node coordinates, one node per row.
  * `elementblocks`: Element blocks is an array of named tuples, each with the data:

      * `block` = block id,
      * `entdim` = entity dimension,
      * `enttag` = entity tag,
      * `elementtypename` = name of the element type,
      * `elementtype` = numerical element type (as defined by Gmsh),
      * `nnodes` = number of nodes per element,
      * `nelements` = number of elements located on this entity,
      * `etags` = array of element tags,
      * `econn` = array of element connectivities, one element per row.
