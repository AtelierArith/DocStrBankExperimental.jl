```
evaluate(S, obs; <keyword arguments>) -> Number | Tuple
```

Compare output of simulation results for the given system `S` and observation data `obs` with a choice of evaluation metric.

# Arguments

  * `S::Type{<:System}`: type of system to be evaluated.
  * `obs::DataFrame`: observation data to be used for evaluation.

# Keyword Arguments

## Configuration

  * `config=()`: a single configuration for the system (can't be used with `configs`).
  * `configs=[]`: multiple configurations for the system (can't be used with `config`).

## Layout

  * `index=nothing`: variables to construct index columns of the output; default falls back to `context.clock.time`.
  * `target`: variables to construct non-index columns of the output.

## Evaluation

  * `metric=nothing`: evaluation metric (`:rmse`, `:nrmse`, `:mae`, `:mape`, `:ef`, `:dr`); default is RMSE.

Remaining keyword arguments are passed down to `simulate` with regard to running system `S`.

See also: [`simulate`](@ref), [`calibrate`](@ref), [`@config`](@ref)

# Examples

```julia-repl
julia> @system S(Controller) begin
           a => 19 ~ preserve(u"m/hr", parameter)
           b(a) ~ accumulate(u"m")
       end;

julia> obs = DataFrame(time=10u"hr", b=200u"m");

julia> configs = @config !(:S => :a => [19, 21]);

julia> evaluate(S, obs; configs, target=:b, stop=10u"hr")
10.0 m
```
