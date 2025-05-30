```
monitor(lk::Link, onsignal...)
monitor(t::Task, onsignal...; timeout::Real=5.0, pollint::Real=0.1)
```

`lk`で表されるアクターまたはタスク`t`の監視を開始し、[`Down`](@ref)を送信するか、失敗した場合に`onsignal...`を実行します。

# パラメータ

  * `onsignal...`: `Down`シグナルに対して取るアクション: 

      * 空の場合、警告が表示されます;
      * 引数が1つの`f`の場合、`f(msg.reason)`で実行されます;
      * `f, args...`の場合、`f(args..., msg.reason)`で実行されます。
  * `timeout::Real=5.0`: タスクを何秒間監視するか。これを超えると、理由`:timed_out`の[`Down`](@ref)が送信されます。
  * `pollint::Real=0.1`: タスク監視のためのポーリング間隔（秒）。
