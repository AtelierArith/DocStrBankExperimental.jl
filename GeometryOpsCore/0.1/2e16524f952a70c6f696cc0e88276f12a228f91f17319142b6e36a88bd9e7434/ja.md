```
apply(f, target::Union{TraitTarget, GI.AbstractTrait}, obj; kw...)
```

ジオメトリ、フィーチャー、フィーチャーコレクション、またはそれらのネストされたベクターを再構築するには、`target`トレイトに対して関数`f`を使用します。

`f(target_geom) => x` ここで `x` も `target`トレイトを持つか、置き換え可能なトレイトを持ちます。たとえば、`PolgonTrait`を`MultiPointTrait`に置き換えると、外側のオブジェクトが`MultiPolygonTrait`を持っている場合は失敗しますが、`FeatureTrait`を持っている場合は成功します。

ターゲットトレイトよりも「浅い」オブジェクトは常に完全に再構築されます。たとえば、ターゲットが`PolygonTrait`であり、フィーチャーに保持されている場合、`FeatureCollectionTrait`の`FeatureTrait`の`Vector`のようにです。これらは常にGeoInterfaceのジオメトリ/フィーチャー/フィーチャーコレクションです。しかし、「深い」オブジェクトは変更されないか、`f`が返すGeoInterface互換オブジェクトのままである可能性があります。

結果は、`f`に依存する値を持つ機能的に類似したジオメトリです。

  * `threaded`: `true`または`false`。マルチスレッドを使用するかどうか。デフォルトは`false`です。
  * `crs`: ジオメトリに添付するCRS。デフォルトは`nothing`です。
  * `calc_extent`: `true`または`false`。範囲を計算するかどうか。デフォルトは`false`です。

## 例

任意のフィーチャーまたはジオメトリ、またはそれらの反復可能なオブジェクト内の点の順序を反転させます：

```julia
import GeoInterface as GI
import GeometryOps as GO
geom = GI.Polygon([GI.LinearRing([(1, 2), (3, 4), (5, 6), (1, 2)]),
                   GI.LinearRing([(3, 4), (5, 6), (6, 7), (3, 4)])])

flipped_geom = GO.apply(GI.PointTrait, geom) do p
    (GI.y(p), GI.x(p))
end
```
