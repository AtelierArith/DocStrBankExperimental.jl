rect(f::Function, args...)

`Layered.Rect`型の`GeometricObject`を含む形状を作成し、後で指定された`Function` `f`に渡される引数として、すべてのトレーリング引数を依存関係として保存します。`f`は`Layered.Rect`型の`GeometricObject`を返す必要があり、描画プロセス中に形状に対して`solve!`が呼び出されたときに評価されます。
