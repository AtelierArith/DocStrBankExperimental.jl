```
SetCellRule <: Rule
```

Abstract supertype for rules that can manually write to any cells of the grid that they need to.

For example, `SetCellRule` is applied with like this, here simply adding 1 to the current cell:

```jldoctest SetCellRule
using DynamicGrids
struct MySetCellRule{R,W} <: SetCellRule{R,W} end

function applyrule!(data::AbstractSimData, rule::MySetCellRule{R,W}, state, I) where {R,W}
    # Add 1 to the cell 10 up and 10 accross
    I, isinbounds = inbounds(I .+ 10)
    isinbounds && add!(data[W], 1, I...)
    return nothing
end
# output
applyrule! (generic function with 1 method)
```

Note the `!` bang - this method alters the state of `data`.

To update the grid, you can use atomic operators [`add!`](@ref), [`sub!`](@ref), [`min!`](@ref), [`max!`](@ref), and [`and!`](@ref), [`or!`](@ref) for `Bool`. These methods safely combined writes from all grid cells - directly using `setindex!` would cause bugs.

It there are multiple write grids, you will need to get the grid keys from type parameters, here `W1` and `W2`:

```jldoctest SetCellRule
function applyrule(data, rule::MySetCellRule{R,Tuple{W1,W2}}, state, I) where {R,W1,W2}
    add!(data[W1], 1, I...)
    add!(data[W2], 2, I...)
    return nothing
end
# output
applyrule (generic function with 1 method)
```

DynamicGrids guarantees that:

  * values written to anywhere on the grid do not affect other cells in   the same rule at the same timestep.
  * values written to anywhere on the grid are available to the next rule in the   sequence, or in the next timestep if there are no remaining rules.
  * if atomic operators like `add!` and `sub!` are always used to write to the grid,   race conditions will not occur on any hardware.
