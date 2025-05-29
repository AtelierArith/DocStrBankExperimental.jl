```
StopWhenEntryChangeLess
```

特定のフィールドの変化が特定の閾値未満であるかどうかを評価します

## フィールド

  * `field`:     特定の[`AbstractManoptSolverState`](@ref)のサブタイプにおける対応するフィールドを追跡するためのシンボル
  * `distance`:  2つの可能な`field`の値の間の距離を計算する関数 `(problem, state, v1, v2) -> R`
  * `storage`:   前の`field`の値を保存するための[`StoreStateAction`](@ref)
  * `threshold`: 距離がこの値未満のときに停止することを示す閾値

# 内部フィールド

  * `at_iteration`: 停止の指示が発生したイテレーションを保存

[`AbstractManoptSolverState`](@ref)内から最適化変数の変化のノルムを見て停止する閾値を保存します。すなわち、`get_iterate(o)`。ストレージには[`StoreStateAction`](@ref)が使用されます。

# コンストラクタ

```
StopWhenEntryChangeLess(
    field::Symbol
    distance,
    threshold;
    storage::StoreStateAction=StoreStateAction([field]),
)
```
