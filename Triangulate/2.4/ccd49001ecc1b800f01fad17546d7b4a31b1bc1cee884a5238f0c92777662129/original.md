```julia
mutable struct TriangulateIO
```

Julia version of Triangle's triangulateio structure.

Used to  pass data into and  out of the triangulate()  procedure.  The arrays are stored  in column major order with the first index being the local number in a triangle or segment and the second index being the index in the element count. This exactly corresponds to  the layout  used in  Triangle. This  means that  all data  in this structure are passed from/to triangle without copying.

Arrays are used to store points, triangles, markers, and so forth.       

Description of fields:

  * `pointlist::Matrix{Float64}`: An array of point coordinates with `size(pointlist,1)==2`. `pointlist' must always point to a list of points. **Mandatory**.

  * `pointattributelist::Matrix{Float64}`: An array of point attributes. There can be several attributes per point. Optional for input.

  * `pointmarkerlist::Vector{Int32}`: An array of point markers. Optional for input.

  * `trianglelist::Matrix{Int32}`: An array of triangle corners. The first three entries of each column describe the three nodes of the triangle in counterclockwise manner. They are followed by  any other nodes if the triangle represents a nonlinear element. This means that without specifying the 'o2' switch, each column contains three node indices, while in the opposite case, each column contains six entries: the three triangle vertices and the three edge mindpoint nodes.

    **Mandatory if the 'r' switch is used**. In this case `trianglelist' must point to a list of triangles with optional higher order nodes.

  * `triangleattributelist::Matrix{Float64}`: An array of triangle attributes. There can be several attributes per triangle. Optional on input.

  * `trianglearealist::Vector{Float64}`: An array of triangle area constraints. Input only.

    **Mandatory if both the 'r' and the 'a'  switch (with no number following) are used.**

  * `neighborlist::Matrix{Int32}`: An array of triangle neighbors. `size(neighborlist,1)==3` triangle.  Output only.

  * `segmentlist::Matrix{Int32}`: An array of segment endpoints. `size(segmentlist,1)==2`

    **Mandatory if the 'p' switch is used**.

  * `segmentmarkerlist::Vector{Int32}`: An array of segment markers. Optional on input. If not set then segment markers on output default to zero.

  * `holelist::Matrix{Float64}`: An array of holes. Holes are marked by some point from within the hole. Input only, although the array pointer is copied to the output structure for convenience.

    Used if  the 'p' switch is used without the 'r' switch.

  * `regionlist::Matrix{Float64}`: An array of regional attributes and area constraints.

    Used if  the 'p' switch is used without the 'r' switch.

    Each of the columns of this array contains the constraint's x and y coordinates are at indices [1] and [2], followed by the regional attribute at index [3], followed by the maximum area at index [4]. So we have `size(regionlist,1)==4`. Note that each regional attribute is used only if you select the 'A' switch, and each area constraint is used only if you select the 'a' switch (with no number following), but omitting one of these switches does not change the memory layout. Input only, although the pointer is copied to the output structure for convenience.

  * `edgelist::Matrix{Int32}`: An array of edge endpoints. `sizeof(edgelist,1)==2`.  Output only.

  * `edgemarkerlist::Vector{Int32}`: An array of edge markers; Output   only.

  * `normlist::Matrix{Float64}`: An array of normal vectors, used for infinite rays in Voronoi diagrams. For each finite edge in a Voronoi diagram, the normal vector written is the  zero vector.  `sizeof(normlist,1)==2`. Output only.
