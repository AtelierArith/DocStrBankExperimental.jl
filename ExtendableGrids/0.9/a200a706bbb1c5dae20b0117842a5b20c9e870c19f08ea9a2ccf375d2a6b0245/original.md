```julia
subgrid(
    parent,
    subregions::AbstractArray;
    transform,
    boundary,
    project
) -> ExtendableGrids.ExtendableGrid

```

Create subgrid from list of regions.

  * `parent`: parent grid
  * `subregions`:  Array of subregions
  * `transform` (kw parameter): transformation function between  grid and subgrid coordinates acting on one point.  Default: `copytransform`
  * `boundary`: if true, create codimension 1 subgrid from boundary region.
  * `project`: project coordinates onto  subgrid dimension

A subgrid is of type `ExtendableGrid` and stores two additional components: [`ParentGrid`](@ref) and [`NodeInParent`](@ref)
