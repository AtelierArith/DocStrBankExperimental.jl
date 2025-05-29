```
read_fasta_alignment(filename::AbstractString, max_gap_fraction::Real)
```

`filename`に含まれる複数配列アライメントの整数の`L × M`行列を返します（`L`は配列の長さ、`M`は配列の数）。この行列には、ギャップ（`-`）の割合が`max_gap_fraction`以下のすべての配列が含まれます。
