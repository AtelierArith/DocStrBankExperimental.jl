```
Cellrule <: Rule
```

A `Rule` that only writes and uses a state from single cell of the read grids, and has its return value written back to the same cell(s).

This limitation can be useful for performance optimisation, such as wrapping rules in [`Chain`](@ref) so that no writes occur between rules.

`CellRule` is defined with :

```jldoctest yourcellrule
using DynamicGrids
struct MyCellRule{R,W} <: CellRule{R,W} end
# output
```

And applied as:

```jldoctest yourcellrule
function applyrule(data, rule::MyCellRule, state, I)
    state * 2
end
# output
applyrule (generic function with 1 method)
```

As the index `I` is provided in `applyrule`, you can use it to look up [`Aux`](@ref) data. 
