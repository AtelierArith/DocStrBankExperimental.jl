```
ft_latex_sn(m_digits::Int, [columns::AbstractVector{Int}]) -> Function
```

Format the numbers of the elements in the `columns` to a scientific notation using LaTeX. The number is first printed using `Printf` functions with the `g` modifier and then converted to the LaTeX format. The number of digits in the mantissa can be selected by the argument `m_digits`.

If `m_digits` is a `Vector`, `columns` must be also be a `Vector` with the same number of elements. If `m_digits` is a `Integer`, and `columns` is not specified (or is empty), the format will be applied to the entire table.  Otherwise, if `m_digits` is a `String` and `columns` is a `Vector`, the format will be applied only to the columns in `columns`.

!!! info
    This formatter will be applied only to the cells that are of type `Number`.

