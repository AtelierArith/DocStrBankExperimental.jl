`Tabular(cols)`

LaTeX環境 `\begin{tabular}{cols} ... \end{tabular}` のためのものです。

`cols` は `tabular` の列仕様構文に従う必要があります。

# 例

```jldoctest
julia> using LaTeXTabulars

julia> Tabular("l" * "r"^5)
Tabular("lrrrrr")
```
