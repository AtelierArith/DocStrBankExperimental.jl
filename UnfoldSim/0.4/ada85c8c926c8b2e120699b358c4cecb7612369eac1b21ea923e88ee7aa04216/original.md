```
generate_events(design::SingleSubjectDesign)
generate_events(rng::AbstractRNG, design::SingleSubjectDesign)
```

Generate the events DataFrame based on `design.conditions` and afterwards apply `design.event_order_function`.

If `design.conditions` is `nothing`, a single trial is simulated with a column `:dummy` and content `:dummy` - this is for convenience.

# Examples

```julia-repl
julia> using Random # for shuffling
julia> using StableRNGs

julia> design = SingleSubjectDesign(;
           conditions = Dict(:A => ["small", "large"], :B => range(1, 5, length = 3)),
           event_order_function = shuffle,
       );

# Variant 1: Without specifying an RNG, MersenneTwister(1) will be used for the shuffling specified as `event_order_function`.
julia> generate_events(design)
6×2 DataFrame
 Row │ A       B       
     │ String  Float64 
─────┼─────────────────
   1 │ large       5.0
   2 │ large       1.0
   3 │ large       3.0
   4 │ small       1.0
   5 │ small       3.0
   6 │ small       5.0

# Variant 2: Use a custom RNG.
julia> generate_events(StableRNG(1), design)
6×2 DataFrame
 Row │ A       B       
     │ String  Float64 
─────┼─────────────────
   1 │ large       5.0
   2 │ large       3.0
   3 │ small       1.0
   4 │ small       3.0
   5 │ large       1.0
   6 │ small       5.0
```
