```
RecordTime <: RecordAction
```

現在のイテレーション中に経過した時間を記録します。

可能な3つのモードは次のとおりです。

  * `:cumulative` タイマーをリセットせずに時間を記録します
  * `:iterative` タイマーをリセットしながら時間を記録します
  * `:total` アルゴリズムの最後にのみ時間を記録します（[`stop_solver!`](@ref）を参照）

デフォルトは `:cumulative` で、リストにないシンボルはこのモードを使用することがデフォルトです。

# コンストラクタ

```
RecordTime(; mode::Symbol=:cumulative)
```
