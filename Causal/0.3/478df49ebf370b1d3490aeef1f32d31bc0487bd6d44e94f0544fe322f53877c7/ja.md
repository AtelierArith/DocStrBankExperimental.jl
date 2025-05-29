```julia
mutable struct TaskManager{T, S, IP, OP, CB}
```

`TaskManager`を`pairs`で構築します。`pairs`は、キーがコンポーネントで値がコンポーネントタスクである辞書です。コンポーネントタスクは、コンポーネントに対応して構築されます。`TaskManager`は、コンポーネントに対応して起動されたコンポーネントタスクを追跡するために使用されます。

# フィールド

  * `pairs::Dict`: ノード-タスクペア
  * `handshakeport::Any`: タスクマネージャのハンドシェイクポート。ハンドシェイクに使用されます
  * `triggerport::Any`: タスクマネージャのトリガーポート。コンポーネントをトリガーするために使用されます
  * `callbacks::Any`: コールバックセット。 [`Callback`](@ref)
  * `name::Symbol`: タスクマネージャの名前
  * `id::Base.UUID`: 一意の識別子

```
