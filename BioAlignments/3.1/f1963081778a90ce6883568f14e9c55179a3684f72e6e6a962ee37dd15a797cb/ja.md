```
alignment(alignment_result)
```

結果があれば、[`PairwiseAlignment`](@ref)としてアライメントを返します。[`Alignment`](@ref)を取得するには、関数をネストします。例えば、`alignment(alignment(alignment_result))`のように。この関数は、後方互換性の理由から`Alignment`の代わりに`PairwiseAlignment`を返します。

関連情報: `hasalignment`
