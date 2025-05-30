```
DynamicScheduler (aka :dynamic)
```

デフォルトの動的スケジューラです。与えられたコレクションをチャンクに分割し、リクエストされた操作を並行して実行するためにチャンクごとにタスクを生成します。タスクはJuliaの動的スケジューラによってスレッドに割り当てられ、非粘着性であるため、スレッド間で移動することができます。

一般的に柔軟性があり、負荷分散を提供でき、他のマルチスレッドコードと組み合わせることができるため、好まれます。

## キーワード引数:

  * `nchunks::Integer` または `ntasks::Integer` (デフォルト `nthreads(threadpool)`):

      * チャンクの数（したがって並行タスクの数）を決定します。
      * `nchunks`を増やすことで[負荷分散](https://en.wikipedia.org/wiki/Load_balancing_(computing))に役立ちますが、オーバーヘッドが増えるという代償があります。`nchunks <= nthreads()`の場合、負荷分散のためのチャンクが不足します。
      * `nchunks < nthreads()`を設定することは、利用可能なスレッドのサブセットのみを使用する効果的な方法です。
  * `chunksize::Integer` (デフォルト未設定)

      * 希望するチャンクサイズを指定します（チャンクの数の代わりに）。
      * オプションの`chunksize`と`nchunks`/`ntasks`は**相互排他的**です（正の整数は1つだけでなければなりません）。
  * `minchunksize::Union{Integer, Nothing}` (デフォルト `nothing`)

      * チャンクのサイズの下限を設定します。この引数は`nchunks`よりも優先されるため、例えば`treduce(+, 1:10; nchunks=10, minchunksize=5)`は`2`チャンクのみで操作します。
  * `split::Union{Symbol, OhMyThreads.Split}` (デフォルト `OhMyThreads.Consecutive()`):

      * コレクションがチャンクに分割される方法を決定します（`chunking=true`の場合）。デフォルトでは、各チャンクは連続した要素で構成され、順序が維持されます。
      * 詳細および利用可能なオプションについては[ChunkSplitters.jl](https://github.com/JuliaFolds2/ChunkSplitters.jl)を参照してください。また、ユーザーが`Consecutive()`の代わりに`:consecutive`を、`RoundRobin()`の代わりに`:roundrobin`を渡すことも許可しています。
      * `split=OhMyThreads.RoundRobin()`の場合、要素の順序は維持されず、リデューサ関数は結合的であるだけでなく**可換的**でなければなりません！
  * `chunking::Bool` (デフォルト `true`):

      * 入力要素がチャンクにグループ化されるかどうかを制御します（`true`）またはしないか（`false`）。
      * `chunking=false`の場合、引数`nchunks`/`ntasks`、`chunksize`、および`split`は無視され、入力要素はそのまま「チャンク」として扱われます。したがって、入力要素ごとに1つの並行タスクが生成されます。入力によっては、これが**多くの(!)タスク**を生成する可能性があり、コストがかかることに注意してください！
  * `threadpool::Symbol` (デフォルト `:default`):

      * 可能なオプションは`:default`と`:interactive`です。
      * 高優先度プール`:interactive`は非常に注意して使用する必要があります。なぜなら、このスレッドプール上のタスクは`yield`せずに長時間実行されるべきではなく、[ハートビート](https://en.wikipedia.org/wiki/Heartbeat_(computing))プロセスに干渉する可能性があるからです。
