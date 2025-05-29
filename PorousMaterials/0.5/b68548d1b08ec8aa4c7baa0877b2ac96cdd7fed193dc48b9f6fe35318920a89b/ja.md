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

一連のグランドカノニカル（μVT）モンテカルロシミュレーションを実行します。引数は [`μVT_sim`](@ref) と同じで、これは裏で実行される関数です。例外として、圧力の配列を渡します。吸着等温線は段階的に計算され、前のシミュレーションの終了構成（分子の配列）が次のシミュレーションの出発点として渡されます。`pressures` の順序は尊重されます。各シミュレーションに良い出発点を与えることで（次の圧力が前の圧力と大きく異ならない場合）、モンテカルロシミュレーションで平衡に達するために必要なバーナーサイクルの数を減らすことができます。また、各圧力でμVTシミュレーションを並行して実行する [`adsorption_isotherm`](@ref) も参照してください。
