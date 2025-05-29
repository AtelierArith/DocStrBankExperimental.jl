```
find_sequence(label::AbstractString, aln::AbstractAlignment)
```

`aln`内の名前`label`のシーケンスを見つけ、`(index, sequence)`を返します。シーケンスの数に応じてスケールします。ラベルに一致する最初のシーケンスを返します。

!!! シーケンスの*ビュー*を返します。
