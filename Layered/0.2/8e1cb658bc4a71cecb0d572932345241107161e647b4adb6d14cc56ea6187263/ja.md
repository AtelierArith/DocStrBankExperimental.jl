paths!(f::Function, layer::Layer, args...)

`Layered.Path`型の`GeometricObject`を含む複数の形状を作成し、トレーリング引数を依存関係として保存します。これらは、与えられた`Function` `f`に引数として渡されるもので、`GeometricObject`の型`Layered.Path`を返す必要があります。これは、描画プロセス中に形状に対して`solve!`が呼び出されたときに評価されます。この関数は、作成された形状を与えられた`Layer` `layer`に追加します。
