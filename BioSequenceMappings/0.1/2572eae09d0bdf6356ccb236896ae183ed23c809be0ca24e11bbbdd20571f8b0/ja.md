```
match_sequences(pattern, aln::AbstractAlignment)
```

`aln`内の`label`と一致する名前のシーケンスを見つけ、`(indices, sequences)`を返します。シーケンスは列として返されます。

!!! シーケンスの*ビュー*を返します。
