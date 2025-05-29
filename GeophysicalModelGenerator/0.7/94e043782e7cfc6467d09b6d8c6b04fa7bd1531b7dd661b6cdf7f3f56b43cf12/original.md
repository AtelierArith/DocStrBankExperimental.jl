```
add_sphere!(Phase, Temp, Grid::AbstractGeneralGrid; cen::Tuple = (0,0,-1), radius::Number,
        phase = ConstantPhase(1).
        T=nothing, cell=false )
```

Adds a sphere with phase & temperature structure to a 3D model setup.  This simplifies creating model geometries in geodynamic models

# Parameters

  * `Phase` - Phase array (consistent with Grid)
  * `Temp`  - Temperature array (consistent with Grid)
  * `Grid` - LaMEM grid structure (usually obtained with read*LaMEM*inputfile)
  * `cen` - center coordinates of sphere
  * `radius` - radius of sphere
  * `phase` - specifies the phase of the box. See `ConstantPhase()`,`LithosphericPhases()`
  * `T` - specifies the temperature of the box. See `ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`
  * `cell` - if true, `Phase` and `Temp` are defined on cell centers

# Example

Sphere with constant phase and temperature:

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
julia> add_sphere!(Phases,Temp,Grid, cen=(0,0,-1), radius=0.5, phase=ConstantPhase(2), T=ConstantTemp(800))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Create Cartesian model
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
