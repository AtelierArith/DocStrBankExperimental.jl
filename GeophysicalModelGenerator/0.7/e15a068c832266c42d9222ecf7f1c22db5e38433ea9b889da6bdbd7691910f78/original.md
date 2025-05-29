```
add_stripes!(Phase, Grid::AbstractGeneralGrid;
    stripAxes       = (1,1,0),
    stripeWidth     =  0.2,
    stripeSpacing   =  1,
    Origin          =  nothing,
    StrikeAngle     =  0,
    DipAngle        =  10,
    phase           =  ConstantPhase(3),
    stripePhase     =  ConstantPhase(4),
    cell            = false)
```

Adds stripes to a pre-defined phase (e.g. added using add_box!)

# Parameters

  * `Phase` - Phase array (consistent with Grid)
  * `Grid` -  grid structure (usually obtained with read*LaMEM*inputfile, but can also be other grid types)
  * `stripAxes` - sets the axis for which we want the stripes. Default is (1,1,0) i.e. X, Y and not Z
  * `stripeWidth` - width of the stripe
  * `stripeSpacing` - space between two stripes
  * `Origin` - the origin, used to rotate the box around. Default is the left-front-top corner
  * `StrikeAngle` - strike angle
  * `DipAngle` - dip angle
  * `phase` - specifies the phase we want to apply stripes to
  * `stripePhase` - specifies the stripe phase
  * `cell` - if true, `Phase` and `Temp` are defined on centers

# Example

Example: Box with striped phase and constant temperature & a dip angle of 10 degrees:

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
julia> add_stripes!(Phases, Grid, stripAxes=(1,1,1), stripeWidth=0.2, stripeSpacing=1, Origin=nothing, StrikeAngle=0, DipAngle=10, phase=ConstantPhase(3), stripePhase=ConstantPhase(4))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Create Cartesian model
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # Save model to paraview
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
