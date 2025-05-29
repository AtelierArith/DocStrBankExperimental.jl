```
AnalysisCallback(semi; interval=0,
                        save_analysis=false,
                        output_directory="out",
                        analysis_filename="analysis.dat",
                        extra_analysis_errors=Symbol[],
                        extra_analysis_integrals=())
```

Analyze a numerical solution every `interval` time steps and print the results to the screen. If `save_analysis`, the results are also saved in `joinpath(output_directory, analysis_filename)`.

Additional errors can be computed, e.g. by passing `extra_analysis_errors = (:l2_error_primitive, :linf_error_primitive)` or `extra_analysis_errors = (:conservation_error,)`.

If you want to omit the computation (to safe compute-time) of the [`default_analysis_errors`](@ref), specify `analysis_errors = Symbol[]`. Note: `default_analysis_errors` are `:l2_error` and `:linf_error` for all equations. If you want to compute `extra_analysis_errors` such as `:conservation_error` solely, i.e., without `:l2_error, :linf_error` you need to specify `analysis_errors = [:conservation_error]` instead of `extra_analysis_errors = [:conservation_error]`.

Further scalar functions `func` in `extra_analysis_integrals` are applied to the numerical solution and integrated over the computational domain. Some examples for this are [`entropy`](@ref), [`energy_kinetic`](@ref), [`energy_internal`](@ref), and [`energy_total`](@ref). You can also write your own function with the same signature as the examples listed above and pass it via `extra_analysis_integrals`. See the developer comments about `Trixi.analyze`, `Trixi.pretty_form_utf`, and `Trixi.pretty_form_ascii` for further information on how to create custom analysis quantities.

In addition, the analysis callback records and outputs a number of quantities that are useful for evaluating the computational performance, such as the total runtime, the performance index (time/DOF/rhs!), the time spent in garbage collection (GC), or the current memory usage (alloc'd memory).
