```
calibrate(S, obs; <keyword arguments>) -> Config | OrderedDict
```

Obtain a set of parameters for the given system `S` that simulates provided observation `obs` closely as possible. A multitude of simulations are conducted with a differing combination of parameter sets specified by the range of possible values and the optimum is selected based on a choice of evaluation metric. Internally, differential evolution algorithm from BlackboxOptim.jl is used.

# Arguments

  * `S::Type{<:System}`: type of system to be calibrated.
  * `obs::DataFrame`: observation data to be used for calibration.

# Keyword Arguments

## Configuration

  * `config=()`: a single base configuration for the system (can't be used with `configs`).
  * `configs=[]`: multiple base configurations for the system (can't be used with `config`).

## Layout

  * `index=nothing`: variables to construct index columns of the output; default falls back to `context.clock.time`.
  * `target`: variables to construct non-index columns of the output.

## Calibration

  * `parameters`: parameters with a range of boundary values to be calibrated within.
  * `metric=nothing`: evaluation metric (`:rmse`, `:nrmse`, `:mae`, `:mape`, `:ef`, `:dr`); default is RMSE.

## Multi-objective

  * `weight=nothing`: weights for calibrating multiple targets; default assumes equal weights.
  * `pareto=false`: returns a dictionary containing Pareto frontier instead of a single solution satisfying multiple targets.

## Advanced

  * `optim=()`: extra options for `BlackBoxOptim.bboptimize`.

Remaining keyword arguments are passed down to `simulate` with regard to running system `S`.

See also: [`simulate`](@ref), [`evaluate`](@ref), [`@config`](@ref)

# Examples

```julia-repl
julia> @system S(Controller) begin
           a => 0 ~ preserve(parameter)
           b(a) ~ accumulate
       end;

julia> obs = DataFrame(time=10u"hr", b=200);

julia> p = calibrate(S, obs; target=:b, parameters=:S => :a => (0, 100), stop=10)
...
Config for 1 system:
  S
    a = 20.0
```
