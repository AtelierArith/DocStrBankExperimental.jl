```
afmesh(xaf, yaf, chord, twist, paxis, xbreak, webloc, segments, webs; ds=nothing, dt=nothing, ns=nothing, nt=nothing, wns=4, wnt=nothing)
```

Create structural mesh for airfoil.  The airfoil coordinates define the meshing density tangential to the airfoil. Whereas the number of layers defines the resolution normal to the airfoil. All segments are meshed with the same resolution in the normal direction, using the number of grid points as defined by segment with the most layers.

**Arguments**

  * `xaf, yaf::Vector{float}`: points defining airfoil start at trailing edge and traverse counterclockwise back to trailing edge (can be blunt or sharp T.E.)
  * `chord::float`: chord length
  * `twist::float`: twist angle (rad)
  * `paxis::float`: pitch axis (normalized by chord). e.g., 0.25 means twist about quarter chord.
  * `xbreak::Vector{float}`: x-locations, normalized by chord, defining break points between segments. must start at 0 and end at 1. e.g., [0, 0.2, 0.4, 0.7, 1.0] defines 4 segments.
  * `webloc::Vector{float}`: x-locations, normalized by chord, defining web centers (and length of vector is number of webs).  e.g., [0.25, 0.55] means there is a web at 25% chord and a second web at 55% chord.
  * `segments::Vector{Vector{Layer}}`: A Layer defines a ply (or multiple plys with the same material/orientation).  At a given x location the ply stack (segment) is defined a vector of layers starting from outside surface towards inside. Segments then is a vector of these segments that defines properties between segments as defined by xbreak.
  * `webs::Vector{Vector{Layer}}`: same structure as segments, except each inner vector is from left to right (although this is usually symmetric), and each outer vector is for a separate web
  * `ds::float`: if provided, airfoil spacing will be resampling with approximately this spacing, normalized by chord.  e.g., 0.01 will have points on the airfoil roughly 1% chord apart.
  * `dt::float`: if provided, thickness will be resampled with this maximum mesh size (thickness is absolute). Note that the total number of cells remains constant along airfoil, so most thicknesses will be much less.  e.g., 0.01 will target a maximum mesh thickness of 0.01 (absolute).
  * `ns::vector{int}`: if provided, rather than use a targert size ds, we specify the number of cells to use in each segment.  This is desirable for gradient-based optimization, if airfoil coordinates are changed, so that during resizing operations the  mesh stretch/shrinks rather than experiencing discrete jumps.  For example, ns=[15, 20, 40, 30] would use 15 elements between xbreak[1] and xbreak[2] and so on.
  * `nt::vector{vector{int}}`: if provided, defines how many elements to use across tangential direction.  Again, prefered over dt for gradient-based optimization, if the thicknesses are changed during optimization.  each entry defines how many cells to put in that layer following order of original layup.  for example, nt=[[1, 2, 1], [1, 3]] would use 1 element, 2 elements (subdivide), then 1 elements over first sector, and so on.
  * `wns::int`: discretization level for number of elements vertically along web.
  * `wnt::vector{vector{int}}`: same definition as nt but for the webs

**Returns**

  * `nodes::Vector{Node{Float64}}`: nodes for this mesh
  * `elements::Vector{MeshElement{Float64}}`: elements for this mesh
