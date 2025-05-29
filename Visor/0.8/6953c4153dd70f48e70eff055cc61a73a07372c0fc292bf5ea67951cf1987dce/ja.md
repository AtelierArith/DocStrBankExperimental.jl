```
supervise(processes::Vector{<:Supervised};
          intensity::Int=DEFAULT_INTENSITY,
          period::Int=DEFAULT_PERIOD,
          strategy::Symbol=:one_for_one,
          terminateif::Symbol=:empty,
          handler::Union{Nothing, Function}=nothing,
          wait::Bool=true)::Supervisor
```

ルートスーパーバイザーは、監視された `processes` のファミリーを開始します。

ルートスーパーバイザーを返すか、`wait` が true の場合はスーパーバイザーの終了を待ちます。

# 引数

  * `intensity::Int`: `period` 秒間に許可される最大再起動回数。
  * `period::Int`: 再起動の強度を制御する時間間隔。
  * `strategy::Symbol`: 再起動戦略を定義します：

      * `:one_for_one`: 終了したタスクのみが再起動されます。
      * `:one_for_all`: 子タスクが終了した場合、他のすべてのタスクが終了し、その後、終了したタスクを含むすべての子タスクが再起動されます。
      * `:rest_for_one`: 子タスクが終了した場合、残りの子タスク（すなわち、終了したプロセスの開始順序に従った子タスク）が終了します。その後、終了した子タスクと残りの子タスクが再起動されます。
      * `:one_terminate_all`: 子タスクが終了した場合、残りのタスクが同時に終了します（起動順序は尊重されません）。
  * `terminateif::Symbol`:

      * `:empty`: すべての子タスクが終了したときにスーパーバイザーを終了します。
      * `:shutdown`: シャットダウン時にスーパーバイザーを終了します。
  * `handler`: プロセスイベントが発生したときに呼び出されるプロトタイプ `fn(process, event)` を持つコールバック関数：

プロセスタスクが例外をスローしたときと、`ProcessFatal` 理由でプロセスが終了したとき。

  * `wait::Bool`: 監視されたノードの終了を待ちます。

```julia
    children = [process(worker, args=(15,"myid"))]
    supervise(children)
```
