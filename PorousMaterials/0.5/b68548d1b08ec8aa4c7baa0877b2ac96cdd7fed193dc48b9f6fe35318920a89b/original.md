```
results = stepwise_adsorption_isotherm(xtal, molecule_templates, temperature, pressures,
                              ljff; n_sample_cycles=5000,
                              n_burn_cycles=5000, sample_frequency=1,
                              verbose=true, ewald_precision=1e-6, eos=:ideal,
                              write_adsorbate_snapshots=false,
                              snapshot_frequency=1, calculate_density_grid=false,
                              density_grid_dx=1.0, density_grid_species=nothing,
                              density_grid_sim_box::Bool=true,
                              results_filename_comment="", show_progress_bar=false)
```

Run a set of grand-canonical (μVT) Monte Carlo simulations in series. Arguments are the same as [`μVT_sim`](@ref), as this is the function run behind the scenes. An exception is that we pass an array of pressures. The adsorption isotherm is computed step- wise, where the ending configuration from the previous simulation (array of molecules) is passed into the next simulation as a starting point. The ordering of `pressures` is honored. By giving each simulation a good starting point, (if the next pressure does not differ significantly from the previous pressure), we can reduce the number of burn cycles required to reach equilibrium in the Monte Carlo simulation. Also see [`adsorption_isotherm`](@ref) which runs the μVT simulation at each pressure in parallel.
