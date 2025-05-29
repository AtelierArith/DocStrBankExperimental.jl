```
RecordSubsolver <: RecordAction
```

現在のサブソルバーの記録を、サブステートで[`get_record`](@ref)を呼び出すことによって記録します。

# フィールド

  * `records`: 記録された値を格納するための配列
  * `symbols`: [`get_record`](@ref)の引数。デフォルトでは1つのシンボル`:Iteration`のみですが、`:Stop`アクションも記録するように設定できます。

# コンストラクタ

```
RecordSubsolver(; record=[:Iteration,], record_type=eltype([]))
```
