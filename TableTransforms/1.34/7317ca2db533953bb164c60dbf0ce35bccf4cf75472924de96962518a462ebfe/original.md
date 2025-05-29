```
Coerce(col₁ => S₁, col₂ => S₂, ..., colₙ => Sₙ)
```

Return a copy of the table, ensuring that the scientific types of the columns match the new specification.

```
Coerce(S)
```

Coerce all columns of the table with scientific type `S`.

This transform uses the `DataScienceTraits.coerce` function. Please see their docstring for more details.

# Examples

```julia
using DataScienceTraits
Coerce(1 => Continuous, 2 => Continuous)
Coerce(:a => Continuous, :b => Continuous)
Coerce("a" => Continuous, "b" => Continuous)
```
