```
extend(X::AbstractSheaf, cover::AbstractCover, sections::AbstractVector)
```

与えられたセクションに制限される一意のセクションにセクションのコレクションを拡張します。`sections`ベクトルは、`enumerate(cover)`と同じ順序でインデックス付けされる必要があります。
