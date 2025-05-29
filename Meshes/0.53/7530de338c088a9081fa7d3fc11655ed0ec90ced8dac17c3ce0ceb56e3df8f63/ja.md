```
HalfEdgeTopology(elements; sort=true)
HalfEdgeTopology(halfedges; nelems=nothing)
```

半エッジから構築された、接続性のベクトル `elements` または `halfedges` のペアのベクトルに基づく、向きのある2次元多様体のためのデータ構造です。

オプション `sort` は、一貫性のない向き（すなわち、時計回りと反時計回りの混合）の場合に、隣接優先順序で要素をソートするために使用できます。

オプション `nelems` は、サイズヒントとしての `elements` の近似数を指定するために使用できます。

## 例

トップフェイスのリストから半エッジトポロジーを構築します：

```julia
elements = connect.([(1,2,3),(3,2,4,5)])
topology = HalfEdgeTopology(elements)
```

他にも [`Topology`](@ref) を参照してください。

## 参考文献

  * Kettner, L. (1999). [Using generic programming for designing a data structure for polyhedral surfaces](https://www.sciencedirect.com/science/article/pii/S0925772199000073)

### 注意事項

半エッジには2種類存在します（Kettner 1999）。この実装は、発生要素を分割する最も一般的なタイプです。

`halfedges` のベクトルと `half4elem` の辞書、`half4vert` の辞書を組み合わせることで、最適な時間でトポロジー関係を取得できます。この場合、`half4vert[i]` は、頭が `i` に等しい `halfedges` の半エッジのインデックスを返します。同様に、`half4elem[i]` は、要素 `i` にある `halfedges` の半エッジのインデックスを返します。さらに、辞書 `edge4pair` は、与えられた頂点のペアに対するエッジ（すなわち、2つの半分）のインデックスを返します。

メッシュの `elements` がすでに一貫した向きを持っている場合、最大のパフォーマンスのために `sort` オプションを無効にすることができます。
