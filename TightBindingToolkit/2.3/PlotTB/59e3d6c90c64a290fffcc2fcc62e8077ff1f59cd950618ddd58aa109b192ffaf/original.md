```julia
Plot_UnitCell!(uc::UnitCell ; range::Int64 = 1, bond_cmp::Symbol = :matter, sub_cmp::Symbol = :rainbow, plot_conjugate::Bool=false, plot_labels::Vector{String} = unique(getproperty.(uc.bonds, :label)), plot_arrows::Bool = true, bond_opacity::Float64 = 0.6, site_size::Float64 = 16.0, bond_thickness::Tuple{Float64, Float64} = (4.0, 2.0), bond_rev::Bool=false, plot_lattice::Bool=false)
```

Function to plot the `UnitCell`. 

  * `range` determines the range of UnitCells plotted in real-space. default is ±1.
  * `bond_cmp` determines the colorScheme chosen to differentiate b.w different hopping types.
  * `plot_conjugate` switches on whether the conjugate of the bonds in `UnitCell` are also plotted or not.
  * `sub_cmp` is the choden colorScheme for the different sublattices.
  * `plot_labels` is the vector of bond labels to be plotted.
  * `plot_arrows` : whether to plot arrows on bonds.
  * `bond_opacity` : alpha value of bonds being plotted.
  * `bond_thickness` : linewidth of bonds being plotted.
  * `site_size`: size of sublattice points.
  * `plot_lattice`: plot bonds on all sites or only on one unit cell.
