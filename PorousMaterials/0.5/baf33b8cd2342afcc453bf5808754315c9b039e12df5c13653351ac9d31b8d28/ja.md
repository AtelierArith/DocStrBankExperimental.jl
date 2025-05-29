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

並列で一連のグランドカノニカル（μVT）モンテカルロシミュレーションを実行します。引数は [`μVT_sim`](@ref) と同じで、これは裏で並列に実行される関数です。唯一の例外は、圧力の配列を渡し、単一の種のみを考慮することです。Juliaに複数のコアへのアクセスを提供するには、スクリプトを `julia -p 4 mysim.jl` として実行し、例えば4つのコアを割り当てます。詳細は [Parallel Computing](https://docs.julialang.org/en/stable/manual/parallel-computing/#Parallel-Computing-1) を参照してください。
