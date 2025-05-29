line!(f::Function, layer::Layer, args...)

`Layered.Line`型の`GeometricObject`を含む形状を作成し、後で与えられた`Function` `f`に引数として渡される依存関係として、すべてのトレーリング引数を保存します。`f`は`Layered.Line`型の`GeometricObject`を返す必要があり、描画プロセス中に形状に対して`solve!`が呼び出されると評価されます。この関数は、作成された形状を指定された`Layer` `layer`に追加します。
