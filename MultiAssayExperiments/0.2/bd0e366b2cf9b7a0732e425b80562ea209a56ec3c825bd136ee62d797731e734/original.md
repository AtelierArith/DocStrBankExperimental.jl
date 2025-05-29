```
filtersamplemap!(x; samples = nothing, experiments = nothing, colnames = nothing)
```

Modifies `samplemap(x)` in place by filtering based on [`filtersamplemap`](@ref). A reference to the modified `x` is returned.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> filtersamplemap!(x; samples = ["Patient1", "Patient2"]);

julia> samplemap(x)
8×3 DataFrame
 Row │ sample    experiment  colname 
     │ String    String      String  
─────┼───────────────────────────────
   1 │ Patient1  foo         foo1
   2 │ Patient1  foo         foo2
   3 │ Patient1  foo         foo3
   4 │ Patient2  foo         foo4
   5 │ Patient2  foo         foo5
   6 │ Patient2  foo         foo6
   7 │ Patient2  bar         bar1
   8 │ Patient2  bar         bar2
```
