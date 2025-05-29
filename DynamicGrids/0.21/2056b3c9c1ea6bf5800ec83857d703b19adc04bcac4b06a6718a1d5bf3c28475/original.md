```
Call <: CellRule

Cell(f)
Cell{R,W}(f)
```

A [`CellRule`](@ref) that applies a function `f` to the `R` grid value,  or `Tuple` of values, and returns the `W` grid value or `Tuple` of values.

Especially convenient with `do` notation.

## Example

Double the cell value in grid `:a`:

```jldoctest Cell
using DynamicGrids
simplerule = Cell{:a}() do data, a, I
    2a
end
# output
Cell{:a,:a}(
    f = var"#1#2"
)
```

`data` is an [`AbstractSimData`](@ref) object, `a` is the cell value, and `I` is a `Tuple` holding the cell index.

If you need to use multiple grids (a and b), use the `R` and `W` type parameters. If you want to use external variables, wrap the whole thing in a `let` block, for performance. This rule sets the new value of `b` to the value of `a` to `b` times scalar `y`:

```jldoctest Cell
y = 0.7
rule = let y = y
    rule = Cell{Tuple{:a,:b},:b}() do data, (a, b), I
        a + b * y
    end
end
# output
Cell{Tuple{:a, :b},:b}(
    f = var"#3#4"{Float64}
)
```
