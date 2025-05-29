```
add_slab!(Phase, Temp, Grid::AbstractGeneralGrid,  trench::Trench; phase = ConstantPhase(1), T = nothing, cell=false)
```

Adds a curved slab with phase & temperature structure to a 3D model setup.

# Parameters

  * `Phase`   - Phase array (consistent with Grid)
  * `Temp`    - Temperature array (consistent with Grid)
  * `Grid`    - grid structure (can be any of the grid types in `GMG`)
  * `trench`  - Trench structure
  * `phase`   - specifies the phase of the box. See `ConstantPhase()`,`LithosphericPhases()`
  * `T`       - specifies the temperature of the box. See `ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`,`LithosphericTemp()`
  * `cell`    - if true, `Phase` and `Temp` are defined on cells

# Examples

Example 1) Slab

```julia-repl
julia> x     = LinRange(0.0,1200.0,128);
julia> y     = LinRange(0.0,1200.0,128);
julia> z     = LinRange(-660,50,128);
julia> Cart  = CartData(xyz_grid(x, y, z));
julia> Phase = ones(Int64,size(Cart));
julia> Temp  = fill(1350.0,size(Cart));
# Define the trench:
julia> trench= Trench(Start = (400.0,400.0), End = (800.0,800.0), θ_max = 45.0, direction = 1.0, n_seg = 50, Length = 600.0, Thickness = 80.0, Lb = 500.0, d_decoupling = 100.0, type_bending =:Ribe)
julia> phase = LithosphericPhases(Layers=[5 7 88], Phases = [2 3 4], Tlab=nothing)
julia> TsHC  = HalfspaceCoolingTemp(Tsurface=20.0, Tmantle=1350, Age=30, Adiabat=0.4)
julia> add_slab!(Phase, Temp, Cart, trench, phase = phase, T = TsHC)
```
