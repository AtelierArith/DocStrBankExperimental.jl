```julia
plot_FS!(Ham::Hamiltonian , bz::BZ , Efermi::Vector{Float64} , band_index::Vector{Int64})--> Plots.plot()
```

Function to draw the fermi surface at `Efermi` for the given `Hamiltonian` on the given `BZ`. 

  * `cmp` determines the colorMap used for the contours.
  * `cbar` determines whether to plot the colorbar or not.
