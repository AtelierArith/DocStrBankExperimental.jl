```
set_macro_timing(::GenericModel, value::Bool)
```

Turn on (if `value`, or off, if `!value`) JuMP's built-in profiling of model construction macros.

Use [`print_macro_timing_summary`](@ref) to display a summary.

## Example

```jldoctest; filter=[r"Total time inside macros: .+ seconds", r"├.+", r"└.+"]
julia> begin
           model = Model()
           set_macro_timing(model, true)
           @variable(model, x[1:2])
           @objective(model, Min, sum(x))
       end;

julia> print_macro_timing_summary(model)
Total time inside macros: 5.33690e-02 seconds
│
├ 2.96490e-02 s [55.55%]
│ ├ REPL[8]:3
│ └ `@variable(model, x[1:2])`
│
└ 2.37200e-02 s [44.45%]
  ├ REPL[8]:4
  └ `@objective(model, Min, sum(x))`
```
