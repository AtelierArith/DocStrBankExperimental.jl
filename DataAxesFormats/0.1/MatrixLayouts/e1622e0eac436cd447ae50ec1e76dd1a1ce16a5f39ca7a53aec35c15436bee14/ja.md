```
transposer(matrix::AbstractMatrix)::AbstractMatrix
transposer(matrix::NamedMatrix)::NamedMatrix
```

これは `LinearAlgebra.transpose!(similar(transpose(m)), m)` の省略形です。つまり、これは行列の転置を返しますが、単にゼロコピーラッパーを使用するのではなく、実際にデータを再配置します。[`relayout!`](@ref)を参照してください。
