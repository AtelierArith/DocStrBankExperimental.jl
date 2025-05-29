```
struct SectorValues{I<:Sector}
```

シングルトン型は、`values(I)`として取得されるインスタンスの型`I`の可能な値に対するイテレータを表します。新しい`I::Sector`については、以下を定義する必要があります。

  * `Base.iterate(::SectorValues{I}[, state])`: 値を反復処理します
  * `Base.IteratorSize(::Type{SectorValues{I}})`: `HasLength()`, `SizeUnknown()` または `IsInfinite()`、これは型`I`の値の数が有限（かつ十分に小さい）か無限であるかに応じて異なります。値の数が多い場合は、`SizeUnknown()`が推奨されます。これは`GenericGradedSpace`の使用を引き起こします。

`IteratorSize(I) == HasLength()`の場合、以下も実装する必要があります。

  * `Base.length(::SectorValues{I})`: 異なる値の数
  * `Base.getindex(::SectorValues{I}, i::Int)`: インデックス`i`と`I`のインスタンスとのマッピング。`SectorValues`イテレータの`i`番目の値を返すフォールバック実装があります。
  * `findindex(::SectorValues{I}, c::I)`: 値`c::I`とインデックス`i::Integer ∈ 1:length(values(I))`との逆マッピング。`SectorValues`イテレータを線形検索するフォールバック実装があります。
