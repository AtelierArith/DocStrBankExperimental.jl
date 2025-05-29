```
generate_events(design::MultiSubjectDesign)
generate_events(rng::AbstractRNG, design::MultiSubjectDesign)
```

Generate the events Dataframe according to `MixedModelsSim.jl`'s `simdat_crossed` function.

Afterwards apply `design.event_order_function` and finally sort by `:subject`. 
Note: No condition can be named `dv` which is used internally in MixedModelsSim / MixedModels as a dummy left-side

# Examples

```julia-repl
julia> using Random # for shuffling
julia> using StableRNGs

julia> design = MultiSubjectDesign(;
                       n_items = 4,
                       n_subjects = 5,
                       both_within = Dict(:condition => ["red", "green"]),
                       event_order_function = shuffle,
                       );

julia> generate_events(StableRNG(1), design)
40×3 DataFrame
 Row │ subject  item    condition 
     │ String   String  String    
─────┼────────────────────────────
   1 │ S1       I2      red
   2 │ S1       I2      green
   3 │ S1       I3      green
  ⋮  │    ⋮       ⋮         ⋮
  38 │ S5       I3      red
  39 │ S5       I2      red
  40 │ S5       I4      green
                   34 rows omitted
```
