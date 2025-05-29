path!(f::Function, layer::Layer, args...)

`Layered.Path` 型の `GeometricObject` を含む形状を作成し、後で指定された `Function` `f` に渡される引数として、すべてのトレーリング引数を依存関係として保存します。`f` は `Layered.Path` 型の `GeometricObject` を返す必要があり、描画プロセス中に形状に対して `solve!` が呼び出されたときに評価されます。この関数は、作成された形状を指定された `Layer` `layer` に追加します。
