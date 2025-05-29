```
order2nside(order::Integer)
```

与えられたオーダーに対するNSIDEの値を返します。指定されたオーダーが無効な場合は、`DomainError`例外をスローします。

[`Healpix.Resolution`](@ref)オブジェクトを作成した場合、フィールド`nside`を通じてNSIDEの値にアクセスできます。

また、[`nside2order`](@ref)も参照してください。
