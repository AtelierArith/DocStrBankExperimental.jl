```
struct TaskOutput <: QuEraSchema
```

マシン上での `QuEraTaskSpecification` の実行結果。

[`execute`](@ref) 関数の出力。

# フィールド

  * `task_status_code::Int`: タスクステータス
  * `shot_outputs::Vector{ShotOutput}`: 原子がリュードベリ状態/基底状態にあるかのバイナリの事前および事後ショットのシーケンスを含む。
