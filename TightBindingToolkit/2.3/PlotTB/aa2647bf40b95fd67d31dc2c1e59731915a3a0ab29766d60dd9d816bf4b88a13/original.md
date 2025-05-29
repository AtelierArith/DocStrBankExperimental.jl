```julia
Plot_Fields!(uc::UnitCell ; OnSiteMatrices::Vector{Matrix{ComplexF64}}=SpinMats((uc.localDim - 1)//2), scale::Float64 = 1.0, range::Int64 = 1, cmp::Symbol = :thermal, field_thickness::Float64 = 1.0, field_opacity::Float64 = 0.6, use_lookup::Bool = false, site_size::Float64 = 12.0)
```

Function to plot the Fields of the UnitCell. ``

  * `range` determines the range of UnitCells plotted in real-space. default is ±1.
  * `cmp` determines the colorScheme of chosen to differentiate b.w different fields.
  * `field_thickness` linewidth of the fields being plotted.
  * `field_opacity` : alpha value of the fields being plotted.
  * `use_lookup` : if you have implemented on-site terms using Bonds and not fields.
  * `OnSiteMatrices` : the matrices w.r.t which the lookup table on each site will be decomposed to get a vector field on each site.
  * `site_size` : size of sublattice points being plotted.
