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

Calculate final aerodynamic results. Reference point is in the kite body (KB) frame.

Returns:     Dict: Results including forces, coefficients and distributions
