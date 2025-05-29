```
qec_merge(data...) -> Vector{Dict}
```

Merge simulation run data.

Run data is expected in the format specified by [`qec_run`](@ref). Merged data is grouped by: `(:code, :n_k_d, :error_model, :decoder, :error_probability, :time_steps, :measurement_error_probability)`. The scalar values: `:n_run`, `:n_success`, `:n_fail`, `:error_weight_total` and `:wall_time` are summed. The vector value: `:n_logical_commutations` is summed element-wise. The vector value: `:custom_totals` is summed element-wise for scalar elements and concatenated along dimension 1 (`vcat`) for array elements. The values: `:logical_failure_rate` and `:physical_error_rate` are recalculated. The value `:error_weight_pvar` is *not* currently recalculated and is therefore omitted.

# Examples

```jldoctest; filter = r":wall_time +=> \d*\.?\d*"
julia> using Qecsim.BasicModels, Qecsim.GenericModels, Logging

julia> code, error_model, decoder = FiveQubitCode(), BitFlipErrorModel(), NaiveDecoder();

julia> data = Dict[];

julia> with_logger(NullLogger()) do # disable logging for brevity in doctest
           push!(data, qec_run(code, error_model, decoder, 0.08, 19; max_runs=100))
           push!(data, qec_run(code, error_model, decoder, 0.08, 23; max_runs=100))
       end;

julia> qec_merge(data...)
1-element Vector{Dict{Symbol, Any}}:
 Dict(:measurement_error_probability => 0.0, :error_probability => 0.08, :time_steps => 1, :error_weight_total => 83, :n_logical_commutations => [11, 3], :wall_time => 0.0028351720000000004, :n_k_d => (5, 1, 3), :error_model => "Bit-flip", :n_success => 189, :logical_failure_rate => 0.055…)
```
