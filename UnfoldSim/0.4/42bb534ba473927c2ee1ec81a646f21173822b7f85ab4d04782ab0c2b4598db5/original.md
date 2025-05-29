```
SingleSubjectDesign <: AbstractDesign
```

A type for specifying the experimental design for a single subject (based on the given conditions).

Tip: Check the resulting dataframe using the [`generate_events`](@ref) function. 
The number of trials/rows in the output of `generate_events([rng, ]design)` depends on the full factorial of your `conditions`. 
To increase the number of repetitions, e.g. by 5, simply use `RepeatDesign(SingleSubjectDesign(...), 5)`. 
If conditions are omitted (or set to `nothing`), a single trial is simulated with a column `:dummy` and content `:dummy` - this is for convenience.

# Fields

  * `conditions::Dict{Symbol,Vector}`: Experimental conditions, e.g. `Dict(:A => ["a_small","a_big"], :B => ["b_tiny","b_large"])`.
  * `event_order_function = (rng, x) -> x`: Can be used to sort by specifying `sort`, or shuffling by providing `shuffle`, or custom functions following the interface `(rng, x) -> my_shuffle(rng,x)`.   The default is the identify function, i.e. not changing the order of the events.

# Examples

```julia-repl
julia> using StableRNGs # For using the `generate_events` function in a reproducible way

julia> design =
           SingleSubjectDesign(;
               conditions = Dict(
                   :stimulus_type => ["natural", "artificial"],
                   :contrast_level => range(0, 1, length = 5),
               ),
           )
SingleSubjectDesign
  conditions: Dict{Symbol, Vector}
  event_order_function: #10 (function of type UnfoldSim.var"#10#14")

julia> generate_events(StableRNG(1), design)
10×2 DataFrame
 Row │ contrast_level  stimulus_type 
     │ Float64         String        
─────┼───────────────────────────────
   1 │           0.0   natural
   2 │           0.25  natural
   3 │           0.5   natural
  ⋮  │       ⋮               ⋮
   8 │           0.5   artificial
   9 │           0.75  artificial
  10 │           1.0   artificial
                       4 rows omitted
```

See also [`MultiSubjectDesign`](@ref), [`RepeatDesign`](@ref)
