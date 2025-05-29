```
add_box!(Phase, Temp, Grid::AbstractGeneralGrid; xlim::Tuple = (20,100), [ylim::Tuple = (1,10)], zlim::Tuple = (10,80),
        Origin=nothing, StrikeAngle=0, DipAngle=0,
        phase = ConstantPhase(1),
        T=nothing,
        segments=nothing,
        cell=false )
```

Adds a box with phase & temperature structure to a 3D model setup.  This simplifies creating model geometries in geodynamic models

# Parameters

  * `Phase` - Phase array (consistent with Grid)
  * `Temp`  - Temperature array (consistent with Grid)
  * `Grid` -  grid structure (can be any of the grid types in `GMG`)
  * `xlim` -  left/right coordinates of box
  * `ylim` -  front/back coordinates of box [optional; if not specified we use the whole box]
  * `zlim` -  bottom/top coordinates of box
  * `Origin` - the origin, used to rotate the box around. Default is the left-front-top corner
  * `StrikeAngle` - strike angle of slab
  * `DipAngle` - dip angle of slab
  * `phase` - specifies the phase of the box. See `ConstantPhase()`,`LithosphericPhases()`
  * `T` - specifies the temperature of the box. See `ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`,`LithosphericTemp()`
  * `segments` - optional parameter to define multiple ridge segments within the box
  * `cell` - if true, `Phase` and `Temp` are defined on centers

# Examples

Example 1) Box with constant phase and temperature & a dip angle of 10 degrees:

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
julia> add_box!(Phases,Temp,Grid, xlim=(0,500), zlim=(-50,0), phase=ConstantPhase(3), DipAngle=10, T=ConstantTemp(1000))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Create Cartesian model
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```

Example 2) Box with halfspace cooling profile

```julia-repl
julia> Grid = CartData(xyz_grid(-1000:10:1000,0,-660:10:0))
julia> Phases = zeros(Int32,   size(Grid));
julia> Temp   = zeros(Float64, size(Grid));
julia> add_box!(Phases,Temp,Grid, xlim=(0,500), zlim=(-50,0), phase=ConstantPhase(3), DipAngle=10, T=HalfspaceCoolingTemp(Age=30))
julia> Grid = addfield(Grid, (;Phases,Temp));       # Add to Cartesian model
julia> write_paraview(Grid,"LaMEM_ModelSetup")  # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```

Example 3) Box with ridge thermal structure ```julia-repl julia> Grid = CartData(xyz*grid(-1000:10:1000, -1000:10:1000, -660:5:0)) julia> Phases = fill(2, size(Grid)); julia> Temp   = fill(1350.0, size(Grid)); julia> segments = [((-500.0, -1000.0), (-500.0, 0.0)),                     ((-250.0, 0.0), (-250.0, 200.0)),                     ((-750.0, 200.0), (-750.0, 1000.0))]; julia> lith = LithosphericPhases(Layers=[15 55], Phases=[1 2], Tlab=1250); julia> add*box!(Phases, Temp, Grid; xlim=(-1000.0, 0.0), ylim=(-500.0, 500.0),                  zlim=(-80.0, 0.0), phase=lith,                  T=SpreadingRateTemp(SpreadingVel=3), segments=segments) julia> Grid = addfield(Grid, (; Phases, Temp));       # Add to Cartesian model julia> write*paraview(Grid, "Ridge*Thermal*Structure")  # Save model to Paraview 1-element Vector{String}:  "Ridge*Thermal_Structure.vts"
