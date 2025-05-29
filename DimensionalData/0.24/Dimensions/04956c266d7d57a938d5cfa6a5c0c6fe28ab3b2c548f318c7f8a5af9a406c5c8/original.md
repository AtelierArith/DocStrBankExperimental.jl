```
Coord <: Dimension
```

A coordinate dimension itself holds dimensions.

This allows combining point data with other dimensions, such as time.

# Example

```julia
julia> using DimensionalData

julia> dim = Coord([(1.0,1.0,1.0), (1.0,2.0,2.0), (3.0,4.0,4.0), (1.0,3.0,4.0)], (X(), Y(), Z()))
Coord ::
  val: Tuple{Float64, Float64, Float64}[(1.0, 1.0, 1.0), (1.0, 2.0, 2.0), (3.0, 4.0, 4.0), (1.0, 3.0,
4.0)]
  lookup: MergedLookup
Coord{Vector{Tuple{Float64, Float64, Float64}}, DimensionalData.MergedLookup{Tuple{X{Colon, AutoLookup{Auto
Order}, NoMetadata}, Y{Colon, AutoLookup{AutoOrder}, NoMetadata}, Z{Colon, AutoLookup{AutoOrder}, NoMetada
ta}}}, NoMetadata}

julia> da = DimArray(0.1:0.1:0.4, dim)
4-element DimArray{Float64,1} with dimensions:
  Coord (): Tuple{Float64, Float64, Float64}[(1.0, 1.0, 1.0), (1.0, 2.0, 2.0), (3.0, 4.0, 4.0), (1.0,
3.0, 4.0)]
    MergedLookup
 0.1
 0.2
 0.3
 0.4

julia> da[Coord(Z(At(1.0)), Y(Between(1, 3)))]
1-element DimArray{Float64,1} with dimensions:
  Coord (): Tuple{Float64, Float64, Float64}[(1.0, 1.0, 1.0)] MergedLookup
 0.1

julia> da[Coord(4)] == 0.4
true

julia> da[Coord(Between(1, 5), :, At(4.0))]
2-element DimArray{Float64,1} with dimensions:
  Coord (): Tuple{Float64, Float64, Float64}[(3.0, 4.0, 4.0), (1.0, 3.0, 4.0)] MergedLookup
 0.3
 0.4
```
