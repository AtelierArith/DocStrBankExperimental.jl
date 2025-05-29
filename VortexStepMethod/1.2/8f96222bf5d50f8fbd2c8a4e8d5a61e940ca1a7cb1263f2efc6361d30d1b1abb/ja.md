```
calculate_results(body_aero::BodyAerodynamics, gamma_new, 
                 density, aerodynamic_model_type::Model,
                 core_radius_fraction, mu,
                 alpha_array, v_a_array,
                 chord_array, x_airf_array,
                 y_airf_array, z_airf_array,
                 va_array, va_norm_array,
                 va_unit_array, panels::Vector{Panel},
                 is_only_f_and_gamma_output::Bool)
```

最終的な空力結果を計算します。基準点は凧の本体 (KB) フレームにあります。

戻り値:     Dict: 力、係数、分布を含む結果
