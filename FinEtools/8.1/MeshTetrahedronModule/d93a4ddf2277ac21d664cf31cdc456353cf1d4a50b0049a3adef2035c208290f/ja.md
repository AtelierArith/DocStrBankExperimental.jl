```
T4block(
    Length::T,
    Width::T,
    Height::T,
    nL::IT,
    nW::IT,
    nH::IT,
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

3Dブロックの四面体メッシュを生成します。

ノード間の均一な間隔で、規則的に配置された4ノードの四面体で、対角線の指定された向きがあります。

メッシュは、各論理矩形セルを5または6の四面体に分割することによって生成されます。向きに応じて、`orientation` = `:a`, `:b` はセルごとに6つの四面体を生成します。 `:ca`, `:cb` はセルごとに5つの四面体を生成します。

範囲 =<0, Length> x <0, Width> x <0, Height>。要素に分割されます: nL x nW x nH。
