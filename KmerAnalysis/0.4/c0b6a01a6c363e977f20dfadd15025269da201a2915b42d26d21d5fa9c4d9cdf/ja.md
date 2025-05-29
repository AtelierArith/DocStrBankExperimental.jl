```
collapse_into_counts!(result::Vector{MerCount{M}}, mers::Vector{M}) where {M<:AbstractMer}
```

メルタイプのベクターからソートされた `MerCount` のベクターを構築します。

これは、より高レベルでより複雑なkmerカウント手順に使用される基本的なカーネル関数です。

これは `collapse_into_counts` と似ていますが、最初の引数はクリアされ、結果で満たされる `result` ベクターです。

!!! note
    入力ベクター `mers` はこのメソッドによってソートされます。

