point!(f::Function, layer::Layer, args...)

`Layered.Point`型の`GeometricObject`を含む形状を作成し、任意の後続引数を依存関係として保存します。これらは、与えられた`Function` `f`に引数として渡される予定で、`Layered.Point`型の`GeometricObject`を返す必要があります。これは、描画プロセス中に形状に対して`solve!`が呼び出されたときに評価されます。この関数は、作成された形状を指定された`Layer` `layer`に追加します。
