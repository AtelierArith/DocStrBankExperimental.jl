beziers(f::Function, args...)

`Layered.Bezier`型の`GeometricObject`を含む形状を作成し、後で与えられた`Function` `f`に引き渡される依存関係として、任意のトレーリング引数を保存します。`f`は`Layered.Bezier`型の`GeometricObject`を返す必要があり、描画プロセス中に形状に対して`solve!`が呼び出されると評価されます。
