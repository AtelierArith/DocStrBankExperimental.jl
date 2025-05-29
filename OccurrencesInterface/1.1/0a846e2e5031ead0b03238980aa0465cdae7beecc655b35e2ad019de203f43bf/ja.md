```
elements(::T) where {T<:AbstractOccurrenceCollection}
```

抽象的な出現コレクションに含まれる要素を返します。これは反復可能なものでなければなりません。未実装の場合のデフォルト値は `nothing` です。インターフェースの独自の実装の一部としてオーバーロードする場合、これは `Vector` を返さなければなりません。
