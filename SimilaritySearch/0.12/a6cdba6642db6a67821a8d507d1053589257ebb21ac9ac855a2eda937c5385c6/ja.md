```
SearchGraphContext(;
    logger=InformativeLog(),
    neighborhood=Neighborhood(),
    hints_callback=DisjointHints(),
    hyperparameters_callback=OptimizeParameters(),
    parallel_block=get_parallel_block(),
    parallel_first_block=parallel_block,
    logbase_callback=1.5,
    starting_callback=8
    knn::Vector{KnnResult} = [KnnResult(16) for _ in 1:Threads.nthreads()]
    beam::Vector{KnnResult} = [KnnResult(16) for _ in 1:Threads.nthreads()]
    sat::Vector{KnnResult} = [KnnResult(16) for _ in 1:Threads.nthreads()]
    vstates::Vector = [VisitedVerticesBits(32) for _ in 1:Threads.nthreads()]
    minbatch::Int = 0
)

SearchGraphContext(ctx::SearchGraphContext;
    logger=ctx.logger,
    neighborhood=ctx.neighborhood,
    hints_callback=ctx.hints_callback,
    hyperparameters_callback=ctx.hyperparameters_callback,
    parallel_block=ctx.parallel_block,
    parallel_first_block=ctx.parallel_first_block,
    logbase_callback=ctx.logbase_callback,
    starting_callback=ctx.starting_callback,
    knn = ctx.knn,
    beam = ctx.beam,
    sat = ctx.sat,
    vstates = ctx.vstates,
    minbatch = 0
)


便利なコンストラクタは次の構造体のためのものです：

struct SearchGraphContext <: AbstractContext
    logger
    neighborhood::Neighborhood
    hints_callback::Union{Nothing,Callback}
    hyperparameters_callback::Union{Nothing,Callback}
    logbase_callback::Float32
    starting_callback::Int32
    parallel_block::Int32
    parallel_first_block::Int32
    knn::Vector{KnnResult} 
    beam::Vector{KnnResult} 
    sat::Vector{KnnResult} 
    vstates::Vector 
    minbatch::Int
end
```

# 引数

  * `logger`: イベントを処理し、ログを記録する方法、主に挿入のため
  * `neighborhood`: 近傍がどのように計算されるかを指定します。詳細は[`Neighborhood`](@ref)を参照してください。
  * `hints_callback`: ヒントを計算するためのコールバックです。詳細はhits.jlを確認してください。
  * `hyperparameters_callback`: 検索のハイパーパラメータを計算するためのコールバックです。詳細は[`OptimizeParameters`](@ref)を参照してください。
  * `logbase_callback`: コールバックを実行するタイミングを制御するためのログベース
  * `starting_callback`: コールバックを実行し始めるタイミング、実行するための最小長
  * `parallel_block`: 並列処理されるブロックのサイズ
  * `parallel_first_block`: 最初に並列処理されるブロックのサイズ
  * `knn`: 結果キャッシュ
  * `beam`: ビームキャッシュ
  * `sat`: satの近傍結果キャッシュ
  * `vstates`: 訪問済み頂点キャッシュ
  * `minbatch`: 各スレッドごとに解決されるクエリの最小数、詳細は[`getminbatch`](@ref)を参照してください。

# 注意事項

  * コールバックは、インデックスが十分に成長するたびに呼び出されるトリガーです。ハイパーパラメータと構造を整えます。
  * 検索グラフは、直接リンクと逆リンクで構成されており、直接リンクは`neighborhood`オブジェクトで制御され、主に近傍がどのように洗練されるかを制御するために使用されます。逆リンクは、頂点が別の頂点の近傍に現れるときに作成されます。
  * `parallel_block`: マルチスレッドアルゴリズムが一度に処理する要素の数であり、利用可能なスレッドの数よりも大きくすることが重要ですが、あまり大きくしすぎると検索グラフの質が低下する可能性があります（スレッドの数の数倍で十分です）。`parallel_block=1`の場合、アルゴリズムは逐次的になります。
  * `parallel_first_block`: 並列処理を実行する前の逐次的な追加の数。
  * 並列処理はブロック内でコールバックをトリガーしません。
  * `SearchGraph`の構築と検索におけるメモリアロケーションを軽減するためのキャッシュのセット。距離関数がこれらの共有リソース（グローバルに定義された）を使用できる他のメトリックインデックスを呼び出すマルチスレッドシナリオで関連します。
