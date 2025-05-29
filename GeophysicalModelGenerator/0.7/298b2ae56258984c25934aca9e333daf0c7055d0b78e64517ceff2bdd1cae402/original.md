make*volc*topo(Grid::LaMEM_grid; center::Array{Float64, 1}, height::Float64, radius::Float64, crater::Float64,             base=0.0m, background=nothing)

Creates a generic volcano topography (cones and truncated cones)

# Parameters

  * Grid - LaMEM grid (created by read*LaMEM*inputfile)
  * center - x- and -coordinates of center of volcano
  * height - height of volcano
  * radius - radius of volcano

# Optional Parameters

  * crater - this will create a truncated cone and the option defines the radius of the flat top
  * base - this sets the flat topography around the volcano
  * background - this allows loading in a topography and only adding the volcano on top (also allows stacking of several cones to get a volcano with different slopes)

# Example

Cylinder with constant phase and temperature:

```julia-repl
julia> Grid = read_LaMEM_inputfile("test_files/SaltModels.dat")
LaMEM Grid:
  nel         : (32, 32, 32)
  marker/cell : (3, 3, 3)
  markers     : (96, 96, 96)
  x           ϵ [-3.0 : 3.0]
  y           ϵ [-2.0 : 2.0]
  z           ϵ [-2.0 : 0.0]
julia> Topo = make_volc_topo(Grid, center=[0.0,0.0], height=0.4, radius=1.5, crater=0.5, base=0.1)
CartData
    size    : (33, 33, 1)
    x       ϵ [ -3.0 : 3.0]
    y       ϵ [ -2.0 : 2.0]
    z       ϵ [ 0.1 : 0.4]
    fields  : (:Topography,)
  attributes: ["note"]
julia> Topo = make_volc_topo(Grid, center=[0.0,0.0], height=0.8, radius=0.5, crater=0.0, base=0.4, background=Topo.fields.Topography)
CartData
    size    : (33, 33, 1)
    x       ϵ [ -3.0 : 3.0]
    y       ϵ [ -2.0 : 2.0]
    z       ϵ [ 0.1 : 0.8]
    fields  : (:Topography,)
  attributes: ["note"]
julia> write_paraview(Topo,"VolcanoTopo")           # Save topography to paraview
Saved file: VolcanoTopo.vts
```
