```
relayout(matrix::AbstractMatrix)::AbstractMatrix
relayout(matrix::NamedMatrix)::NamedMatrix
```

[`relayout!`](@ref) と同様ですが、宛先行列を自動的に割り当てます。`transpose(transposer(matrix))` と同等です。
