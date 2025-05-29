```
simulate(
rng::AbstractRNG,
design::AbstractDesign,
components,
onset::AbstractOnset,
noise::AbstractNoise = NoNoise();
return_epoched = false,
)

simulate(
design::AbstractDesign,
components,
onset::AbstractOnset,
noise::AbstractNoise = NoNoise();
return_epoched = false,
)
```

Simulate continuous or epoched signal, given `design`, [Array of] `component`, `onset` and  optional `noise` and `rng`. Main simulation function.

# Arguments

  * `rng::AbstractRNG` (optional): Random number generator, important to ensure reproducibility.
  * `design::AbstractDesign`: Desired experimental design.
  * `components`: `Component`(s) for the desired signal.
  * `onset::AbstractOnset`: Desired inter-onset distance distribution.
  * `noise::AbstractNoise = NoNoise()` (optional): Desired noise.

# Keyword arguments

  * `return_epoched::Bool = false`: If set to `true` epoched data is returned, otherwise a continuous signal is returned (see also Notes below).

# Returns

  * `(signal, events)::Tuple{Array, DataFrame}`:

      * `signal` : Generated signal. Depending on the design, on the components and on    `return_epoched`, the output can be a 1-D, 2-D, 3-D or 4-D Array.    For example, a 4-D Array would have the dimensions `channels x time x trials x subjects`.
      * `events`: Generated events data frame with latencies.

# Examples

Adapted from the [quickstart tutorial](https://unfoldtoolbox.github.io/UnfoldSim.jl/stable/generated/tutorials/quickstart/) in the UnfoldSim docs.

```julia-repl
julia> using Random # to get an RNG

julia> design =
    SingleSubjectDesign(; conditions = Dict(:cond_A => ["level_A", "level_B"])) |>
    x -> RepeatDesign(x, 10);

julia> component = LinearModelComponent(; 
    basis = [0, 0, 0, 0.5, 1, 1, 0.5, 0, 0],
    formula = @formula(0 ~ 1 + cond_A),
    β = [1, 0.5],
);

julia> onset = UniformOnset(; width = 20, offset = 4);

julia> noise = PinkNoise(; noiselevel = 0.2);

# Variant 1: Use a custom RNG.
julia> data, events = simulate(MersenneTwister(2), design, component, onset, noise);

julia> data
293-element Vector{Float64}:
 -0.013583193323430123
  0.09159433856866195
  ⋮
 -0.25190584567097907
 -0.20179992275876316

julia> events
20×2 DataFrame
 Row │ cond_A   latency 
     │ String   Int64   
─────┼──────────────────
   1 │ level_A        9
   2 │ level_B       20
   3 │ level_A       27
   4 │ level_B       37
  ⋮  │    ⋮        ⋮
  18 │ level_B      257
  19 │ level_A      271
  20 │ level_B      284
         13 rows omitted

# Variant 2: Without specifying an RNG, MersenneTwister(1) will be used for the simulation.
julia> data1, events1 = simulate(design, component, onset, noise);
┌ Warning: No random generator defined, used the default (`Random.MersenneTwister(1)`) with a fixed seed. This will always return the same results and the user is strongly encouraged to provide their own random generator!
```

# Notes

Some remarks on how the noise is added:

  * If `return_epoched = true` and `onset = NoOnset()` the noise is added to the epoched data matrix.
  * If `onset` is not `NoOnset`, a continuous signal is created and the noise is added to this    i.e. this means that the noise won't be the same as in the `onset = NoOnset()` case even if `return_epoched = true`.
  * The case `return_epoched = false` and `onset = NoOnset()` is not possible and therefore    covered by an assert statement.

Additional remarks on the overlap of adjacent signals when `return_epoched = true`:

  * If `onset = NoOnset()` there will not be any overlapping signals in the data because the onset calculation and conversion to a continuous signal is skipped.
  * If an inter-onset distance distribution is given, a continuous signal(potentially with overlap) is constructed and partitioned into epochs afterwards.
