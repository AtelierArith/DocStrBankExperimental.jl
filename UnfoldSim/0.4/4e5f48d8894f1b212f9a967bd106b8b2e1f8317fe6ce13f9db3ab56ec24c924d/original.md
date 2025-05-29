```
MultiSubjectDesign <: AbstractDesign
```

A type for specifying the experimental design for multiple subjects (based on the given random-effects structure).

Tip: Check the resulting dataframe using the [`generate_events`](@ref) function. 
Please note that the number of items `n_items` has to be a multiple of the number of between-item levels. The sample applies for `n_subjects` and the number of between-subject levels.

# Fields

  * `n_subjects::Int`: Number of subjects.
  * `n_items::Int`: Number of items/stimuli (sometimes ≈ trials).
  * `subjects_between::Dict{Symbol,Vector}`: Effects between subjects, e.g. young vs old.
  * `items_between::Dict{Symbol,Vector}`: Effects between items, e.g. natural vs artificial images, (but shown to all subjects if not specified also in `subjects_between`).
  * `both_within::Dict{Symbol,Vector}`: Effects completely crossed i.e. conditions/covariates that are both within-subject and within-item.
  * `event_order_function = (rng, x) -> x`: Can be used to sort, or shuffle the events e.g. `(rng, x) -> shuffle(rng, x)` (or shorter just `event_order_function = shuffle`).   The default is the identify function, i.e. not changing the order of the events.

# Examples

```julia-repl
# Declaring the same condition both between-subject and between-item results in a full between-subject/item design.
julia> design = MultiSubjectDesign(;
                       n_items = 10,
                       n_subjects = 30,
                       subjects_between = Dict(:cond => ["levelA", "levelB"]),
                       items_between = Dict(:cond => ["levelA", "levelB"]),
                       )
MultiSubjectDesign
  n_subjects: Int64 30
  n_items: Int64 10
  subjects_between: Dict{Symbol, Vector}
  items_between: Dict{Symbol, Vector}
  both_within: Dict{Symbol, Vector}
  event_order_function: #3 (function of type UnfoldSim.var"#3#7")

julia> generate_events(StableRNG(1), design)
150×3 DataFrame
 Row │ subject  cond    item   
     │ String   String  String 
─────┼─────────────────────────
   1 │ S01      levelA  I01
   2 │ S01      levelA  I03
   3 │ S01      levelA  I05
  ⋮  │    ⋮       ⋮       ⋮
 148 │ S30      levelB  I06
 149 │ S30      levelB  I08
 150 │ S30      levelB  I10
               144 rows omitted
```

See also [`SingleSubjectDesign`](@ref), [`RepeatDesign`](@ref)
