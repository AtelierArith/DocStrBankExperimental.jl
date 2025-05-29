抽象配線図をGraphMLとしてシリアライズします。

ボックス、ポート、およびワイヤの値のシリアル化は、データ型によってオーバーロードできます（`convert_to_graphml_data`および`convert_from_graphml_data`を参照）。

GraphMLは、グラフデータ形式の分野における事実上および法的な標準に最も近いものであり、さまざまなグラフアプリケーションやライブラリによってサポートされています。GraphMLノード、ポート、およびエッジにJSONデータ属性を許可することにより、GraphML仕様からわずかに逸脱します。

参考文献：

  * GraphML Primer: http://graphml.graphdrawing.org/primer/graphml-primer.html
  * GraphML DTD: http://graphml.graphdrawing.org/specification/dtd.html
