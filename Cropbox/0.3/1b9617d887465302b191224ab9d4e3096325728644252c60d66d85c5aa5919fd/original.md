```
simulate([f,] S[, layout, [configs]]; <keyword arguments>) -> DataFrame
```

Run simulations by making instance of system `S` with given configuration to generate an output in the form of DataFrame. `layout` contains a list of variables to be saved in the output. A layout of single simulation can be specified in the layout arguments placed as keyword arguments. `configs` contains a list of configurations for each run of simulation. Total number of simulation runs equals to the size of `configs`. For a single configuration, `config` keyword argument may be preferred. Optional callback function `f` allows do-block syntax to specify `snatch` argument for finer control of output format.

See also: [`instance`](@ref), [`@config`](@ref)

# Arguments

  * `S::Type{<:System}`: type of system to be simulated.
  * `layout::Vector`: list of output layout definition in a named tuple `(; base, index, target, meta)`.
  * `configs::Vector`: list of configurations for defining multiple runs of simluations.

# Keyword Arguments

## Layout

  * `base=nothing`: base system where `index` and `target` are populated; default falls back to the instance of `S`.
  * `index=nothing`: variables to construct index columns of the output; default falls back to `context.clock.time`.
  * `target=nothing`: variables to construct non-index columns of the output; default includes most variables in the root instance.
  * `meta=nothing`: name of systems in the configuration to be included in the output as metadata.

## Configuration

  * `config=()`: a single configuration for the system, or a base for multiple configurations (when used with `configs`).
  * `configs=[]`: multiple configurations for the system.
  * `seed=nothing`: random seed for resetting each simulation run.

## Progress

  * `stop=nothing`: condition checked before calling updates for the instance; default stops with no update.
  * `snap=nothing`: condition checked to decide if a snapshot of current update is saved in the output; default snaps all updates.
  * `snatch=nothing`: callback for modifying intermediate output; list of DataFrame `D` collected from current update and the instance of system `s` are provided.
  * `verbose=true`: shows a progress bar.

## Format

  * `nounit=false`: remove units from the output.
  * `long=false`: convert output table from wide to long format.

# Examples

```julia-repl
julia> @system S(Controller) begin
           a => 1 ~ preserve(parameter)
           b(a) ~ accumulate
       end;

julia> simulate(S; stop=1)
2×3 DataFrame
 Row │ time       a        b
     │ Quantity…  Float64  Float64
─────┼─────────────────────────────
   1 │    0.0 hr      1.0      0.0
   2 │    1.0 hr      1.0      1.0
```
