```
merge_overlapping_annotations([predicate=TimeSpans.overlaps,] annotations)
```

`onda.annotation@1` 準拠のテーブル `annotations` を与えると、"重なり合う" 連続した `annotations` のエントリが `TimeSpans.shortest_timespan_containing` を使用してマージされた `Vector{MergedAnnotationV1}` を返します。

2 つの連続したアノテーション `a` と `b` が "重なり合う" と見なされるのは、`a.recording == b.recording && predicate(a.span, b.span)` の場合です。マージされたアノテーションの `span` フィールドは、重なり合うソースアノテーションのセットに対して `TimeSpans.shortest_timespan_containing` を呼び出すことで生成されます。

返されるテーブルのすべてのアノテーションには、新しく生成された `id` フィールドと空でない `from` フィールドがあります。出力アノテーションの `from` フィールドに単一の要素しか含まれていない場合、それは提供された `annotations` の個々の非重なりアノテーションに対応します。

この関数は内部的に `Tables.columns(annotations)` を使用して動作するため、`!Tables.columnaccess(annotations)` の場合、遅くなる可能性があり、またはより多くのメモリを必要とすることがあります。

同様の機能を持つ `TimeSpans.merge_spans` も参照してください（アノテーションではなく一般的な時間スパンに対して）。
