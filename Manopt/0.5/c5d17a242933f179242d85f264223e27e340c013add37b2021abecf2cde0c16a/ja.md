```
StopAfterIteration <: StoppingCriterion
```

最大の反復回数の後に停止するための停止基準のファンクタ。

# フィールド

  * `max_iterations`  停止する最大の反復回数を格納します
  * `at_iteration` 停止基準が満たされた反復回数（`i=0`を含む）を示し、満たされていない間は `-1` です。

# コンストラクタ

```
StopAfterIteration(maxIter)
```

`maxIter` 回の反復の後に停止することを示すようにファンクタを初期化します。
