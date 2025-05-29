```
swap!(N::SpeciesInteractionNetwork{<:Partiteness, <:Binary}, ::Type{Generality})
```

次数に制約を持つ置換は、相互作用する種のペア (r1, s1) と新しい茎種 s3 を選び、(r1, s3) に置き換えようとすることで機能します。この関数は、この置換の結果が s1 からの最後の受信リンクを削除しない場合にのみ適用されます。
