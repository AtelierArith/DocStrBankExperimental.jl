```
rand_design_filename(d_rand::RandDesign)
rand_design_filename(d::Design, total_randomisations::Integer, seed::UInt64)
rand_design_filename(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, full_covariance::Bool, ls_type::Symbol, total_randomisations::Integer, seed::UInt64)
```

ランダム化デザインデータに対応するファイル名を説明する文字列を返します。
