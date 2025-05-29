`Tabular(cols)`

For the LaTeX environment `\begin{tabular}{cols} ... \end{tabular}`.

`cols` should follow the column specification syntax of `tabular`.

# Example

```jldoctest
julia> using LaTeXTabulars

julia> Tabular("l" * "r"^5)
Tabular("lrrrrr")
```
