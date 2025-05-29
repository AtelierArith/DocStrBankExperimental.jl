```
design_filename(d::Design)
design_filename(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, full_covariance::Bool, ls_type::Symbol)
```

提供されたデザインデータに対応するファイル名を説明する文字列を返します。
