txt!(f::Function, layer::Layer, args...)

`Layered.Txt` 型の `GeometricObject` を含む形状を作成し、後で与えられた `Function` `f` に引数として渡される依存関係として、任意のトレーリング引数を保存します。`f` は `Layered.Txt` 型の `GeometricObject` を返す必要があり、描画プロセス中に形状に対して `solve!` が呼び出されたときに評価されます。この関数は、作成された形状を与えられた `Layer` `layer` に追加します。
