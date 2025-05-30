```
GreedyScheduler (別名 :greedy)
```

貪欲な動的スケジューラです。要素は共有の作業キューに入れられ、動的で非粘着的なタスクが生成され、各タスクは前のタスクが完了するとすぐにキューから新しい要素を取得して処理します。

要素は非決定的な順序で処理されるため、潜在的な縮小関数は**結合的**であるだけでなく、[可換](https://en.wikipedia.org/wiki/Commutative_property)でなければならず、そうでないと不正確な結果が得られる可能性があります！

遅い不均一な計算の負荷分散には良い選択肢ですが、いくつかの追加のオーバーヘッドが伴います。

## キーワード引数:

  * `ntasks::Int` (デフォルト `nthreads()`):

      * 生成される並列タスクの数を決定します。
      * `ntasks < nthreads()`を設定することは、利用可能なスレッドのサブセットのみを使用する効果的な方法です。
  * `chunking::Bool` (デフォルト `false`):

      * 入力要素が共有の作業キューに入れられる前にチャンクにグループ化されるかどうかを制御します（`true`）またはしないか（`false`）。これは、計算が安価な多くの反復がある場合に特にパフォーマンスを向上させることができます。
      * `nchunks`または`chunksize`が明示的に指定されている場合、`chunking`は自動的に`true`に設定されます。
  * `nchunks::Integer` (デフォルト `10 * nthreads()`):

      * （最終的に共有の作業キューに入れられる）チャンクの数を決定します。
      * `nchunks`を増やすことで[負荷分散](https://en.wikipedia.org/wiki/Load_balancing_(computing))に役立ちます。`nchunks <= nthreads()`の場合、負荷分散のためのチャンクが不足しています。
  * `chunksize::Integer` (デフォルトは設定されていない)

      * 希望するチャンクサイズを指定します（チャンクの数の代わりに）。
      * オプション`chunksize`と`nchunks`は**相互排他的**です（いずれか一方のみが正の整数であることができます）。
  * `minchunksize::Union{Integer, Nothing}` (デフォルト `nothing`)

      * チャンクのサイズの下限を設定します。この引数は`nchunks`よりも優先されるため、例えば`treduce(+, 1:10; nchunks=10, minchunksize=5)`は`2`チャンクのみで操作します。
  * `split::Union{Symbol, OhMyThreads.Split}` (デフォルト `OhMyThreads.RoundRobin()`):

      * コレクションがチャンクに分割される方法を決定します（`chunking=true`の場合）。
      * 詳細および利用可能なオプションについては[ChunkSplitters.jl](https://github.com/JuliaFolds2/ChunkSplitters.jl)を参照してください。また、ユーザーが`Consecutive()`の代わりに`:consecutive`を、`RoundRobin()`の代わりに`:roundrobin`を渡すことも許可しています。
