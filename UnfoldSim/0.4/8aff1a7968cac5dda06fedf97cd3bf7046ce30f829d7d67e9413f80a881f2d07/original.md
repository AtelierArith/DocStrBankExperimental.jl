```
RepeatDesign{T} <: AbstractDesign
```

Repeat a design (and the corresponding events DataFrame) multiple times to mimick repeatedly recorded trials.

Tip: Check the resulting dataframe using the [`generate_events`](@ref) function. Please note that when using an `event_order_function`(e.g. `shuffle`) in a `RepeatDesign`, the corresponding RNG is shared across repetitions and not deep-copied for each repetition. As a result, the order of events will differ for each repetition.

# Fields

  * `design::T`: The experimental design that should be repeated.
  * `repeat::Int = 1`: The number of repetitions.

# Examples

```julia-repl
julia> using StableRNGs # For using the `generate_events` function in a reproducible way

julia> design_once =
           SingleSubjectDesign(;
               conditions = Dict(
                   :stimulus_type => ["natural", "artificial"],
                   :contrast_level => range(0, 1, length = 2),
               ),
               event_order_function = shuffle,
           );

julia> generate_events(StableRNG(1), design_once)
4×2 DataFrame
 Row │ contrast_level  stimulus_type 
     │ Float64         String        
─────┼───────────────────────────────
   1 │            1.0  natural
   2 │            1.0  artificial
   3 │            0.0  natural
   4 │            0.0  artificial

julia> design = RepeatDesign(design_once, 2)
RepeatDesign{SingleSubjectDesign}
  design: SingleSubjectDesign
  repeat: Int64 2

julia> generate_events(StableRNG(1), design)
8×2 DataFrame
 Row │ contrast_level  stimulus_type 
     │ Float64         String        
─────┼───────────────────────────────
   1 │            1.0  natural
   2 │            1.0  artificial
   3 │            0.0  natural
   4 │            0.0  artificial
   5 │            1.0  artificial
   6 │            0.0  natural
   7 │            1.0  natural
   8 │            0.0  artificial
```

See also [`SingleSubjectDesign`](@ref), [`MultiSubjectDesign`](@ref)
