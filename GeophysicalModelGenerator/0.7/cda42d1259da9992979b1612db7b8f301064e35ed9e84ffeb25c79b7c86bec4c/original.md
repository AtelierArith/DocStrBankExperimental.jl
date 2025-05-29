```
add_layer!(Phase, Temp, Grid::AbstractGeneralGrid; xlim::Tuple = (1,100), [ylim::Tuple = (0,20)], zlim::Tuple = (0,-100),
        phase = ConstantPhase(1),
        T=nothing, cell=false )
```

Adds a layer with phase & temperature structure to a 3D model setup. The most common use would be to add a lithospheric layer to a model setup. This simplifies creating model geometries in geodynamic models

# Parameters

  * `Phase` - Phase array (consistent with Grid)
  * `Temp`  - Temperature array (consistent with Grid)
  * `Grid` -  grid structure (usually obtained with read*LaMEM*inputfile, but can also be other grid types)
  * `xlim` -  left/right coordinates of box
  * `ylim` -  front/back coordinates of box
  * `zlim` -  bottom/top coordinates of box
  * `phase` - specifies the phase of the box. See `ConstantPhase()`,`LithosphericPhases()`
  * `T` - specifies the temperature of the box. See `ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`

# Examples

Example 1) Layer with constant phase and temperature

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
julia> add_layer!(Phases,Temp,Grid, zlim=(-50,0), phase=ConstantPhase(3), T=ConstantTemp(1000))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Create Cartesian model
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```

Example 2) Box with halfspace cooling profile

```julia-repl
julia> Grid = read_LaMEM_inputfile("test_files/SaltModels.dat")
julia> Phases = zeros(Int32,   size(Grid.X));
julia> Temp   = zeros(Float64, size(Grid.X));
julia> add_layer!(Phases,Temp,Grid, zlim=(-50,0), phase=ConstantPhase(3), T=HalfspaceCoolingTemp())
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Create Cartesian model
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
