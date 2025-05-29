```
MemoryView{T, M} <: DenseVector{T}
```

`Memory{T}`へのビュー。`MemoryView(x)`を使って、メモリバックされた値`x`から構築します。

`MemoryView`は、サイズがゼロでない限り、連続した有効なCPUメモリを指すことが保証されています。

パラメータ`M`はメモリビューの可変性を制御し、`Mutable`または`Immutable`であり、それぞれエイリアス`MutableMemoryView{T}`および`ImmutableMemoryView{T}`に対応します。

関連情報: `MemoryKind`

# 例

```jldoctest
julia> v = view([1, 2, 3, 4], 2:3);

julia> mem = MemoryView(v)
2-element MutableMemoryView{Int64}:
 2
 3

julia> MemoryView(codeunits("abc")) isa ImmutableMemoryView{UInt8}
true
```

# 拡張ヘルプ

密なメモリにバックされた新しい型`T`は、以下を実装する必要があります：

  * `MemoryView(x::T)`は、`x`からメモリビューを構築します。これは、`x`のメモリが可変である場合、常に`MutableMemoryView`を返すべきです。
  * `MemoryKind(x::T)`、もし`T`が自身のメモリビューと意味的に等しい場合。これには`Vector`、`Memory`、および`Base.CodeUnits{UInt8, String}`が含まれます。もしそうであれば、`x == MemoryView(x)`が成り立つべきです。

`MemoryView(x)`が実装されている場合、`ImmutableMemoryView(x)`は自動的に機能します。たとえ`MemoryView(x)`が可変ビューを返す場合でもです。

`ImmutableMemoryView`を通じてメモリを変更することはできませんが、ビューの存在は、別の変数を通じて同じメモリが変更されるのを防ぐものではありません。

`MemoryView`内のデータの正確なメモリレイアウトは`Memory`のそれに従います。これには、`String`のような配列内の一部の要素がポインタとして保存される可能性があることや、[isbits Union最適化](https://docs.julialang.org/en/v1/devdocs/isbitsunionarrays/)が含まれます。
