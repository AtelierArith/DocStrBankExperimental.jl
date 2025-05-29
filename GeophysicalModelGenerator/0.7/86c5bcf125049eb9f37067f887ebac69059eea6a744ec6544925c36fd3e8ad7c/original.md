```
add_ellipsoid!(Phase, Temp, Grid::AbstractGeneralGrid; cen::Tuple = (-1,-1,-1), axes::Tuple = (0.2,0.1,0.5),
        Origin=nothing, StrikeAngle=0, DipAngle=0,
        phase = ConstantPhase(1).
        T=nothing, cell=false )
```

Adds an Ellipsoid with phase & temperature structure to a 3D model setup.  This simplifies creating model geometries in geodynamic models

# Parameters

  * `Phase` - Phase array (consistent with Grid)
  * `Temp`  - Temperature array (consistent with Grid)
  * `Grid` - LaMEM grid structure (usually obtained with read*LaMEM*inputfile)
  * `cen` - center coordinates of sphere
  * `axes` - semi-axes of ellipsoid in X,Y,Z
  * `Origin` - the origin, used to rotate the box around. Default is the left-front-top corner
  * `StrikeAngle` - strike angle of slab
  * `DipAngle` - dip angle of slab
  * `phase` - specifies the phase of the box. See `ConstantPhase()`,`LithosphericPhases()`
  * `T` - specifies the temperature of the box. See `ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`
  * `cell` - if true, `Phase` and `Temp` are defined on cell centers

# Example

Ellipsoid with constant phase and temperature, rotated 90 degrees and tilted by 45 degrees:

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
julia> add_ellipsoid!(Phases,Temp,Grid, cen=(-1,-1,-1), axes=(0.2,0.1,0.5), StrikeAngle=90, DipAngle=45, phase=ConstantPhase(3), T=ConstantTemp(600))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Create Cartesian model
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
