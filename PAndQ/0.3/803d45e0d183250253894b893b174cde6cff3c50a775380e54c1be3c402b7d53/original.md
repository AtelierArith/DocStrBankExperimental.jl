```
formatter(T)
```

Use as the `formatters` keyword parameter in [`print_table`](@ref).

| `T`               | `formatter(T)(true, _, _)` | `formatter(T)(false, _, _)` |
|:----------------- |:-------------------------- |:--------------------------- |
| `NullaryOperator` | `"⊤"`                      | `"⊥"`                       |
| `String`          | `"tautology"`              | `"contradiction"`           |
| `Char`            | `"T"`                      | `"F"`                       |
| `Bool`            | `"true"`                   | `"false"`                   |
| `Int`             | `"1"`                      | `"0"`                       |

See also [Nullary Operators](@ref nullary_operators).

# Examples

```jldoctest
julia> @atomize print_table(p ∧ q; formatters = formatter(Bool))
┌───────┬───────┬───────┐
│ p     │ q     │ p ∧ q │
├───────┼───────┼───────┤
│ true  │ true  │ true  │
│ false │ true  │ false │
├───────┼───────┼───────┤
│ true  │ false │ false │
│ false │ false │ false │
└───────┴───────┴───────┘

julia> @atomize print_table(p ∧ q; formatters = formatter(Int))
┌───┬───┬───────┐
│ p │ q │ p ∧ q │
├───┼───┼───────┤
│ 1 │ 1 │ 1     │
│ 0 │ 1 │ 0     │
├───┼───┼───────┤
│ 1 │ 0 │ 0     │
│ 0 │ 0 │ 0     │
└───┴───┴───────┘
```
