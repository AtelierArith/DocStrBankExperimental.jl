```
collapse_into_counts(mers::Vector{M}) where {M<:AbstractMer}
```

メルタイプのベクターからソートされた `MerCount` のベクターを構築します。

これは、より高レベルでより複雑なkmerカウント手順に使用される基本的なカーネル関数です。

!!! note
    入力ベクター `mers` はこの方法でソートされます。

