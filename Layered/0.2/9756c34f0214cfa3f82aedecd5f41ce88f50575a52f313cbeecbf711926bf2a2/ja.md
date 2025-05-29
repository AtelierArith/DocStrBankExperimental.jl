arcs!(f::Function, layer::Layer, args...)

`Layered.Arc`型の`GeometricObject`を含む複数の形状を作成し、後で与えられた`Function` `f`に引数として渡される依存関係として、残りの引数を保存します。`f`は`Layered.Arc`型の`GeometricObject`を返す必要があり、描画プロセス中に形状に対して`solve!`が呼び出されると評価されます。この関数は、作成された形状を指定された`Layer` `layer`に追加します。
