```
scaling_filename(scaling_data::AbstractScalingData)
scaling_filename(d::Design, ls_type::Symbol)
scaling_filename(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, ls_type::Symbol)
```

指定された設計データに対応するスケーリングデータのファイル名を説明する文字列を返します。
