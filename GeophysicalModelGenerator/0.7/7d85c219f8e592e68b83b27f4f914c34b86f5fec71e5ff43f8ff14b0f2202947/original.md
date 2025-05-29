```
    add_polygon!(Phase, Temp, Grid::AbstractGeneralGrid; xlim=(), ylim::Tuple = (0.0,0.8), zlim=(), phase = ConstantPhase(1), T=nothing, cell=false )
```

Adds a polygon with phase & temperature structure to a 3D model setup.  This simplifies creating model geometries in geodynamic models

# Parameters

  * `Phase` - Phase array (consistent with Grid)
  * `Temp`  - Temperature array (consistent with Grid)
  * `Grid`  - Grid structure (usually obtained with read*LaMEM*inputfile)
  * `xlim`  - `x`-coordinate of the polygon points, same ordering as zlim, number of points unlimited
  * `ylim`  - `y`-coordinate, limitation in length possible (two values (start and stop))
  * `zlim`  - `z`-coordinate of the polygon points, same ordering as xlim, number of points unlimited
  * `phase` - specifies the phase of the box. See `ConstantPhase()`
  * `T`     - specifies the temperature of the box. See `ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`
  * `cell`  - if true, `Phase` and `Temp` are defined on cell centers

# Example

Polygon with constant phase and temperature:

```julia-repl
julia> Grid = read_LaMEM_inputfile("test_files/SaltModels.dat")
LaMEM Grid:
  nel         : (32, 32, 32)
  marker/cell : (3, 3, 3)
  markers     : (96, 96, 96)
  x           ϵ [-3.0 : 3.0]
  y           ϵ [-2.0 : 2.0]
  z           ϵ [-2.0 : 0.0]
julia> Phases = zeros(Int32,   size(Grid.X));
julia> Temp   = zeros(Float64, size(Grid.X));
julia> add_polygon!(Phase, Temp, Cart; xlim=(0,0, 1.6, 2.0),ylim=(0,0.8), zlim=(0,-1,-2,0), phase = ConstantPhase(8), T=ConstantTemp(30))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Create Cartesian model
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
