arc(f::Function, args...)

`Layered.Arc`型の`GeometricObject`を含む形状を作成し、後で与えられた`Function` `f`に引数として渡される依存関係として、すべてのトレーリング引数を保存します。`f`は`Layered.Arc`型の`GeometricObject`を返す必要があり、描画プロセス中に形状に対して`solve!`が呼び出されると評価されます。
