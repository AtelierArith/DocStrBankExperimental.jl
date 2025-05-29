```julia
mutable struct RawTetGenIO{T}
```

A  structure for  transferring  data  into and  out  of TetGen's internal representation.

The input of TetGen is either a 3D point set, or a 3D piecewise linear complex (PLC), or  a tetrahedral mesh.  Depending on  the input object and the specified  options, the output of TetGen is  either a Delaunay (or weighted Delaunay) tetrahedralization, or a constrained (Delaunay) tetrahedralization, or a quality tetrahedral mesh.

A piecewise  linear complex  (PLC) represents  a 3D  polyhedral domain with  possibly internal  boundaries(subdomains). It  is introduced  in [Miller  et al,  1996].   Basically  it is  a  set  of "cells",  i.e., vertices, edges, polygons, and polyhedra,  and the intersection of any two of its cells is the union of other cells of it.

The 'RawTetGenIO' structure  is a collection of arrays  of data, i.e., points, facets, tetrahedra,  and so forth. All data  are compatible to the representation in C++ and can be used without copying.

  * `pointlist::Matrix`: 'pointlist':  Array of point coordinates with `size(pointlist,1)==3`.

  * `pointattributelist::Matrix`: 'pointattributelist':  Array of point attributes. The number of  attributes per point is determined by  `size(pointattributelist,1)`

  * `pointmtrlist::Matrix`: 'pointmtrlist': An array of metric tensors at points.

  * `pointmarkerlist::Vector{Int32}`: 'pointmarkerlist':  An array of point markers; one integer per point.

  * `tetrahedronlist::Matrix{Int32}`:  'tetrahedronlist': An array of tetrahedron corners represented by indices of points in `pointlist`. Unless option `-o2` is given, one has  `size(tetrahedronlist,1)==4`, i.e. each  column describes the    four     corners    of    a     tetrahedron.     Otherwise, `size(tetrahedronlist,1)==10` and the 4  corners are followed by 6 edge midpoints.

  * `tetrahedronattributelist::Matrix`: 'tetrahedronattributelist':  An array of tetrahedron attributes.

  * `tetrahedronvolumelist::Vector`: 'tetrahedronvolumelist':  An array of constraints, i.e. tetrahedron's  volume;  Input only. This can be used for triggering local refinement.

  * `neighborlist::Matrix{Int32}`: 'neighborlist':  An array of tetrahedron neighbors; 4 ints per element.  Output only.

  * `facetlist::Array{TetGen.RawFacet{T}, 1} where T`: 'facetlist':  An array of facets.  Each entry is a structure of facet.

  * `facetmarkerlist::Vector{Int32}`: 'facetmarkerlist':  An array of facet markers; one int per facet.

  * `holelist::Matrix`: 'holelist':  An array of holes (in volume).  Each hole is given by a  point which lies strictly inside it.

  * `regionlist::Matrix`:  'regionlist': An array of regions (subdomains).  Each region is given by  a seed (point) which lies strictly inside it. For each column,  the point coordinates are  at indices [1], [2] and [3], followed by the regional  attribute at index [4], followed by the maximum volume at index [5].

    ote that each regional attribute is used only if you select the 'A'  switch, and each volume constraint is used only if you select the  'a' switch (with no number following).

  * `facetconstraintlist::Matrix`: 'facetconstraintlist':  An array of facet constraints.  Each constraint specifies a maximum area bound on the subfaces of that facet.  Each column contains  a facet marker at index [1] and its maximum area bound at index [2]. Note: the facet marker is actually an integer.

  * `segmentconstraintlist::Matrix`: 'segmentconstraintlist': An array of segment constraints. Each constraint specifies a maximum length bound on the subsegments of that segment. Each columb consists of the  two endpoints of the segment at index [1] and [2], and the maximum length bound at index [3]. Note the segment endpoints are actually integers.

  * `trifacelist::Matrix{Int32}`: 'trifacelist':  An array of face (triangle) corners.

  * `trifacemarkerlist::Vector{Int32}`: 'trifacemarkerlist':  An array of face markers; one int per face.

  * `edgelist::Matrix{Int32}`: 'edgelist':  An array of edge endpoints.

  * `edgemarkerlist::Array{Int32}`: 'edgemarkerlist':  An array of edge markers.
