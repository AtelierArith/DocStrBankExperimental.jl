polygons!(f::Function, layer::Layer, args...)

`Layered.Polygon`型の`GeometricObject`を含む複数の形状を作成し、トレーリング引数を依存関係として保存します。これらは、与えられた`Function` `f`に引数として渡され、`Layered.Polygon`型の`GeometricObject`を返す必要があります。これらは、描画プロセス中に形状に対して`solve!`が呼び出されたときに評価されます。この関数は、作成された形状を指定された`Layer` `layer`に追加します。
