```
nside2order(nside::Integer)
```

与えられた NSIDE に関連付けられた順序（正の整数）を返します。指定された nside が無効な場合は、`DomainError` 例外をスローします。

[`Healpix.Resolution`](@ref) オブジェクトを作成した場合、フィールド `order` を通じて順序にアクセスできます。

また、[`order2nside`](@ref) も参照してください。
