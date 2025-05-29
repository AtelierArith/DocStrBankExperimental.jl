```
qec_run(
    code, error_model, decoder, p::Real, random_seed=nothing;
    max_runs::Union{Integer,Nothing}=nothing,
    max_failures::Union{Integer,Nothing}=nothing
) -> Dict
```

Execute stabilizer code error-decode-recovery (ideal) simulations many times and return aggregated run data, see [`qec_run_once`](@ref) for details of a single run.

The parameters `code`, `error_model` and `decoder` should be concrete subtypes or duck-typed implementations of [`StabilizerCode`](@ref), [`ErrorModel`](@ref) and [`Decoder`](@ref), respectively.

Simulations are run one or more times as determined by `max_runs` and `max_failures`. If `max_runs` and/or `max_failures` are specified, stop after `max_runs` runs or `max_failures` failures, whichever happens first. If neither is specified, stop after one run.

The returned aggregated data has the following format:

```
Dict(
    :code => "5-qubit"              # label(code)
    :n_k_d => (5, 1, 3)             # nkd(code)
    :time_steps => 1                # always 1 for ideal simulations
    :error_model => "Depolarizing"  # label(error_model)
    :decoder => "Naive"             # label(decoder)
    :error_probability => 0.1       # p
    :measurement_error_probability => 0.0   # always 0.0 for ideal simulations
    :n_run => 100                   # count of runs
    :n_success => 92                # count of successful recoveries
    :n_fail => 8                    # count of failed recoveries
    :n_logical_commutations => [5, 6]   # count of logical_commutations
    :custom_totals => nothing       # sum of custom_values
    :error_weight_total => 55       # sum of error_weight over n_run runs
    :error_weight_pvar => 0.4075    # pvariance of error_weight over n_run runs
    :logical_failure_rate => 0.08   # n_fail / n_run
    :physical_error_rate => 0.11    # error_weight_total / n_k_d[1] / time_steps / n_run
    :wall_time => 0.00253906        # wall-time for run in fractional seconds
)
```

# Examples

```jldoctest; filter = r":wall_time +=> \d*\.?\d*"
julia> using Qecsim.BasicModels, Qecsim.GenericModels

julia> seed = 7;

julia> data = qec_run(FiveQubitCode(), DepolarizingErrorModel(), NaiveDecoder(), 0.1, seed;
           max_runs=100);
┌ Info: qec_run: starting
│   code = Qecsim.BasicModels.BasicCode(["XZZXI", "IXZZX", "XIXZZ", "ZXIXZ"], ["XXXXX"], ["ZZZZZ"], (5, 1, 3), "5-qubit")
│   error_model = Qecsim.GenericModels.DepolarizingErrorModel()
│   decoder = Qecsim.GenericModels.NaiveDecoder(10)
│   p = 0.1
│   random_seed = 7
│   max_runs = 100
└   max_failures = nothing
[ Info: qec_run: rng=MersenneTwister(7)
[ Info: qec_run: complete: data=Dict{Symbol, Any}(:error_weight_pvar => 0.4075000000000001, :time_steps => 1, :n_logical_commutations => [5, 6], :error_weight_total => 55, :wall_time => 0.002539058, :n_k_d => (5, 1, 3), :error_model => "Depolarizing", :physical_error_rate => 0.11, :measurement_error_probability => 0.0, :error_probability => 0.1, :n_success => 92, :logical_failure_rate => 0.08, :custom_totals => nothing, :code => "5-qubit", :decoder => "Naive", :n_fail => 8, :n_run => 100)

julia> data
Dict{Symbol, Any} with 17 entries:
  :error_weight_pvar             => 0.4075
  :time_steps                    => 1
  :n_logical_commutations        => [5, 6]
  :error_weight_total            => 55
  :wall_time                     => 0.00253906
  :n_k_d                         => (5, 1, 3)
  :error_model                   => "Depolarizing"
  :physical_error_rate           => 0.11
  :measurement_error_probability => 0.0
  :error_probability             => 0.1
  :n_success                     => 92
  :logical_failure_rate          => 0.08
  :custom_totals                 => nothing
  :code                          => "5-qubit"
  :decoder                       => "Naive"
  :n_fail                        => 8
  :n_run                         => 100
```
