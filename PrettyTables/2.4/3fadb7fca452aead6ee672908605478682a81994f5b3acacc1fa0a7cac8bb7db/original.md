```
ft_round(digits::Union{Int, AbstractVector{Int}}, [columns::AbstractVector{Int}]) -> Function
```

Round the elements in the `columns` to the number of `digits`.

If `digits` is a `Vector`, `columns` must be also be a `Vector` with the same number of elements. If `digits` is a `Number`, and `columns` is not specified (or is empty), the rounding will be applied to the entire table.  Otherwise, if `digits` is a `Number` and `columns` is a `Vector`, the elements in the columns `columns` will be rounded to the number of digits `digits`.
