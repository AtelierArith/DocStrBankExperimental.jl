```
results = adsorption_isotherm(xtal, molecule_templates, temperature, 
                              partial_pressures,
                              ljff; n_sample_cycles=5000,
                              n_burn_cycles=5000, sample_frequency=1,
                              verbose=true, ewald_precision=1e-6, eos=:ideal,
                              write_adsorbate_snapshots=false,
                              snapshot_frequency=1, calculate_density_grid=false,
                              density_grid_dx=1.0, density_grid_species=nothing,
                              density_grid_sim_box=true,
                              results_filename_comment="", show_progress_bar=false)
```

Run a set of grand-canonical (μVT) Monte Carlo simulations in parallel. Arguments are the same as [`μVT_sim`](@ref), as this is the function run in parallel behind the scenes. The only exception is that we pass an array of pressures, and we only consider a single species. To give Julia access to multiple cores, run your script as `julia -p 4 mysim.jl` to allocate e.g. four cores. See [Parallel Computing](https://docs.julialang.org/en/stable/manual/parallel-computing/#Parallel-Computing-1).
