```
Resource{T}(capacity)
```

Resourceは、制限された容量を持つ[`Deque`](https://juliacollections.github.io/DataStructures.jl/latest/deque/)を実装します。マルチスレッドアプリケーションで使用する場合、ユーザーは`lock-unlock`で修正呼び出しを明示的にラップすることで競合状態を避ける必要があります。

# フィールド

  * `items::Deque{T}`: リソースバッファ
  * `capacity::Number=Inf`: 容量は指定された整数に制限されます。
  * `lock::ReentrantLock`: タスクによるリソースアクセスを調整するためのロック。

# 例

```jldoctest
julia> 
```

!!! note
    `Resource`の完全なインターフェースを使用するには、`DataStructures`をロードする必要があります。

