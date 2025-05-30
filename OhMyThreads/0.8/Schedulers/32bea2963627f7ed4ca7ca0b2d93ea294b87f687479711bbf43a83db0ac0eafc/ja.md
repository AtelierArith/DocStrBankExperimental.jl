```
StaticScheduler (aka :static)
```

静的な低オーバーヘッドスケジューラです。与えられたコレクションをチャンクに分割し、リクエストされた操作を並行して実行するためにチャンクごとにタスクを生成します。タスクは事前にスレッドに静的に割り当てられ、*スティッキー*にされます。つまり、割り当てられたスレッドに留まることが保証されます（**タスクの移動はありません**）。

ワークロードが（ほぼ）均一な場合や、オーバーヘッドが低いため小さなワークロードの場合、`DynamicScheduler`よりもパフォーマンスが向上することがあります。ただし、他のマルチスレッドコードとの組み合わせにはあまり適していません。

## キーワード引数:

  * `nchunks::Integer` または `ntasks::Integer`（デフォルト `nthreads()`）:

      * チャンクの数（したがって並行タスクの数）を決定します。
      * `nchunks < nthreads()`を設定することは、利用可能なスレッドのサブセットのみを使用する効果的な方法です。
      * `nchunks > nthreads()`の場合、チャンクはラウンドロビン方式で利用可能なスレッドに分配されます。
  * `chunksize::Integer`（デフォルトは設定されていません）

      * 希望するチャンクサイズを指定します（チャンクの数の代わりに）。
      * `chunksize`と`nchunks`/`ntasks`は**相互排他的**です（非ゼロであるのは1つだけです）。
  * `minchunksize::Union{Integer, Nothing}`（デフォルト `nothing`）

      * チャンクのサイズの下限を設定します。この引数は`nchunks`よりも優先されるため、例えば`treduce(+, 1:10; nchunks=10, minchunksize=5)`は2つのチャンクでのみ操作を行います。
  * `chunking::Bool`（デフォルト `true`）:

      * 入力要素がチャンクにグループ化されるかどうかを制御します（`true`）またはしない（`false`）。
      * `chunking=false`の場合、引数`nchunks`/`ntasks`、`chunksize`、および`split`は無視され、入力要素はそのまま「チャンク」として扱われます。したがって、入力要素ごとに1つの並行タスクが生成されます。入力によっては、これが**多くの(!)タスク**を生成する可能性があり、コストがかかることに注意してください！
  * `split::Union{Symbol, OhMyThreads.Split}`（デフォルト `OhMyThreads.Consecutive()`）:

      * コレクションがチャンクにどのように分割されるかを決定します。デフォルトでは、各チャンクは連続した要素で構成され、順序が維持されます。
      * 詳細および利用可能なオプションについては、[ChunkSplitters.jl](https://github.com/JuliaFolds2/ChunkSplitters.jl)を参照してください。また、ユーザーが`Consecutive()`の代わりに`:consecutive`を、`RoundRobin()`の代わりに`:roundrobin`を渡すことも許可しています。
      * `split=OhMyThreads.RoundRobin()`の場合、要素の順序は維持されず、リデューサ関数は結合的であるだけでなく、**可換的**でなければなりません！
