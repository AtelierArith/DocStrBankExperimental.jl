```
transform(geom::AbstractGeometry, f::Transformation)
transform(
    geom::AbstractGeometry{S};
    origin=zero(Point{S}),
    rot=0°,
    xrefl=false,
    mag=1
)
```

`f`を`geom`に適用することによって得られる新しい`AbstractGeometry`を返します。

一般的な`geom`と変換に対して、`f`をスケーリングされた等距離変換に分解しようとします: `translate ∘ magnify ∘ rotate ∘ reflect_across_xaxis`。その場合、`f`が角度を保持しない場合、`DomainError`がスローされます。

`AbstractGeometry`の具体的なサブタイプは次を実装する必要があります。

```
transform(ent::MyEntity, f::Transformation)
```

ただし、任意の`Transformation`が`MyEntity`に対して有効である必要はありません。たとえば、次のように書くことができます。

```julia
transform(ent::MyEntity, f::Transformation) = transform(ent, ScaledIsometry(f))
function transform(ent::MyEntity, f::ScaledIsometry)
    # ... 変換されたエンティティを作成して返す
end
```

これは、`!preserves_angles(f)`の場合（`f`がスケーリングされた等距離変換でない場合）に`DomainError`をスローします。
