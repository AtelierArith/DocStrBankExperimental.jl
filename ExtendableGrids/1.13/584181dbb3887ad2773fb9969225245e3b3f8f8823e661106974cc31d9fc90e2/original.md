```
subgrid(parent,                                                             
        subregions::AbstractArray;                                          
        transform::T = (a, b) -> a .= b[1:length(a)],
        boundary=false,                                                     
        coordinatesystem=codim1_coordinatesystem(parent[CoordinateSystem]), 
        project=true) where T
```

Create subgrid from list of regions.

  * `parent`: parent grid
  * `subregions`:  Array of subregions which define the subgrid
  * 'support': support of subgrid, default is ON*CELLS but can be also ON*FACES or ON_BFACES to create codimension 1 subgrid from face/bfaces region
  * `boundary`: if true, create codimension 1 subgrid from boundary regions (same as support = ON_BFACES)
  * `transform` (kw parameter): transformation function between  grid and subgrid coordinates acting on one point.
  * `coordinatesystem`: if `boundary==true`, specify coordinate system for the boundary.  Default:  if parent coordinatesystem is cartesian, just the corresponding codim1 coordinatesystem,   otherwise: `nothing`, requiring user specification for use of e.g. CellFinder with the subgrid.
  * `project`: project coordinates onto  subgrid dimension

A subgrid is of type `ExtendableGrid` and stores two additional components: [`ParentGrid`](@ref) and [`NodeParents`](@ref)
