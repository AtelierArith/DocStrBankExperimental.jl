```
add_cylinder!(Phase, Temp, Grid::AbstractGeneralGrid; base::Tuple = (-1,-1,-1.5), cap::Tuple = (-1,-1,-0.5), radius::Number,
        phase = ConstantPhase(1),
        T=nothing, cell=false )
```

Adds a cylinder with phase & temperature structure to a 3D model setup.  This simplifies creating model geometries in geodynamic models

# Parameters

  * `Phase` - Phase array (consistent with Grid)
  * `Temp`  - Temperature array (consistent with Grid)
  * `Grid` - Grid structure (usually obtained with `read_LaMEM_inputfile`)
  * `base` - center coordinate of bottom of cylinder
  * `cap` - center coordinate of top of cylinder
  * `radius` - radius of the cylinder
  * `phase` - specifies the phase of the box. See `ConstantPhase()`,`LithosphericPhases()`
  * `T` - specifies the temperature of the box. See `ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`
  * `cell` - if true, `Phase` and `Temp` are defined on cell centers

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
julia> Phases = zeros(Int32,   size(Grid.X));
julia> Temp   = zeros(Float64, size(Grid.X));
julia> add_cylinder!(Phases,Temp,Grid, base=(-1,-1,-1.5), cap=(1,1,-0.5), radius=0.25, phase=ConstantPhase(4), T=ConstantTemp(400))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Create Cartesian model
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
