```
RecordSubsolver <: RecordAction
```

現在のサブソルバーの記録を、サブステートの[`get_record`](@ref)を呼び出すことで記録します。

# フィールド

  * `records`: 記録された値を格納するための配列
  * `symbols`: [`get_record`](@ref)の引数。デフォルトでは1つのシンボル`:Iteration`のみですが、`:Stop`アクションを記録するために設定することもできます。

# コンストラクタ

```
RecordSubsolver(; record=[:Iteration,], record_type=eltype([]))
```
