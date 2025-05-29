bezier!(f::Function, layer::Layer, args...)

指定された `Function` `f` に渡される依存関係として、任意のトレーリング引数を保存する `Layered.Bezier` 型の `GeometricObject` を含む形状を作成します。この `Function` は `Layered.Bezier` 型の `GeometricObject` を返す必要があり、描画プロセス中に形状に対して `solve!` が呼び出されたときに評価されます。この関数は、作成された形状を指定された `Layer` `layer` に追加します。
