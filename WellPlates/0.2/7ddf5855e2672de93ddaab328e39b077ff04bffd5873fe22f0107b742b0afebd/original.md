```
ingredients(plate[, condition::Symbol])
ingredients(plate, group => value)
```

Get a `Dict` of physical requirements to build a plate. Numeric conditions are summed, non-numerics are counted.

## Grouping

When grouping factors are stored as a separate condition, we can use a special syntax to specify this.

### Examples

```jldoctest
julia> p = plate(96, volume = 100μL, cells = down([:Raji, :DG75], FillLast));
julia> ingredients(p, :cells => :volume)[:Raji]
1200 μL
```
