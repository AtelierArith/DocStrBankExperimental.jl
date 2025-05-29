```
significance(counts::AbstractArray{<:Integer})
```

与えられた $N$ 次元のコンティンジェンシー行列 `counts` に基づいて、ハプロタイプの $χ^2$ 有意性を計算します。

`counts` の構築方法の詳細については、[`linkage(::AbstractArray{<:Integer})`](@ref) または [`occurrence_matrix`](@ref) のドキュメントを参照してください。
