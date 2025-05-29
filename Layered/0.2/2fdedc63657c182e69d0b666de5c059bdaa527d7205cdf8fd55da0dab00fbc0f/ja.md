txts(f::Function, args...)

`Layered.Txt`型の`GeometricObject`を含む形状を作成し、後で与えられた`Function` `f`に引き渡される引数として、すべてのトレーリング引数を依存関係として保存します。`f`は`Layered.Txt`型の`GeometricObject`を返す必要があり、描画プロセス中に形状に対して`solve!`が呼び出されると評価されます。
