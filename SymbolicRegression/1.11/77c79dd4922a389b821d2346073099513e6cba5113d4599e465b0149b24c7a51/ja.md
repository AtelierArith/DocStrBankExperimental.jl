```
equation_search(X, y[; kws...])
```

関数 `f_i` の分散方程式検索を実行し、`f_i(X[:, j]) ≈ y[i, j]` のマッピングを記述します。オプションは `SymbolicRegression.Options(...)` を使用して構成され、キーワード引数として `options` に渡す必要があります。デバッグやプロファイリングに便利な `numprocs=0` で並列処理をオフにすることができます。

# 引数

  * `X::AbstractMatrix{T}`: `y` を予測するための入力データセット。最初の次元は特徴、2 番目の次元は行です。
  * `y::Union{AbstractMatrix{T}, AbstractVector{T}}`: 予測する値。最初の次元は各方程式で予測する出力特徴、2 番目の次元は行です。
  * `niterations::Int=100`: 検索を実行する反復回数。反復回数が多いほど結果が改善されます。
  * `weights::Union{AbstractMatrix{T}, AbstractVector{T}, Nothing}=nothing`: 各 `y` の損失にこの値で重みを付けるオプション（`y` と同じ形状）。
  * `options::AbstractOptions=Options()`: 検索のオプション、使用する演算子、進化のハイパーパラメータなど。
  * `variable_names::Union{Vector{String}, Nothing}=nothing`: `X` の各特徴の名前で、方程式の印刷時に使用されます。
  * `display_variable_names::Union{Vector{String}, Nothing}=variable_names`: 検索中に式を印刷する際に使用する名前ですが、方程式ファイルに保存する際には使用されません。
  * `y_variable_names::Union{String,AbstractVector{String},Nothing}=nothing`: `y` の各出力特徴の名前で、方程式の印刷時に使用されます。
  * `parallelism=:multithreading`: 使用する並列処理モード。オプションは `:multithreading`、`:multiprocessing`、および `:serial` です。デフォルトではマルチスレッドが使用されます。マルチスレッドはメモリを少なく使用しますが、マルチプロセスはマルチノード計算を処理できます。`:multithreading` モードを使用する場合、julia に利用可能なスレッド数が使用されます。`:multiprocessing` を使用する場合、`procs` が未設定の場合は `numprocs` プロセスが動的に作成されます。すでにプロセスを割り当てている場合は、それらを `procs` 引数に渡すと使用されます。シンボルの代わりに文字列を渡すこともできます（例: `"multithreading"`）。
  * `numprocs::Union{Int, Nothing}=nothing`: `equation_search` が自動的にこれを設定する場合に使用するプロセスの数。デフォルトは `4` ですが、任意の数（利用可能なコアの数以下）を選択できます。
  * `procs::Union{Vector{Int}, Nothing}=nothing`: `procs = addprocs()` と `@everywhere` で手動で分散実行を設定した場合、`procs` をこのキーワード引数に渡します。
  * `addprocs_function::Union{Function, Nothing}=nothing`: マルチプロセスを使用する場合（`parallelism=:multiprocessing`）、手動で `procs` を渡さない場合、`addprocs` を使用して動的に割り当てられます。ただし、`addprocs` の代わりに使用するカスタム関数を渡すこともできます。この関数は、使用するプロセスの数と `lazy` キーワード引数を受け取る単一の位置引数を取る必要があります。たとえば、slurm クラスターで設定されている場合、`addprocs_function = addprocs_slurm` を渡すことができます。
  * `heap_size_hint_in_bytes::Union{Int,Nothing}=nothing`: Julia 1.9+ では、Julia プロセスに `--heap-size-hint` フラグを設定し、プロセスが推奨サイズに近づいたときにガーベジコレクションを推奨できます。これは、各プロセスが独立したメモリを持つ長時間実行される分散ジョブにとって重要で、メモリ不足エラーを回避するのに役立ちます。デフォルトでは、`Sys.free_memory() / numprocs` に設定されています。
  * `worker_imports::Union{Vector{Symbol},Nothing}=nothing`: 各ワーカーで追加のモジュールをインポートしたい場合、ここにシンボルのベクターとして渡します。デフォルトでは、必要に応じて自動的にいくつかの拡張がロードされます。
  * `runtests::Bool=true`: 検索を開始する前に（簡単な）テストを実行して、ホスト環境に関連する方程式検索中に問題が発生するかどうかを確認するかどうか。
  * `saved_state=nothing`: すでに `equation_search` を実行していて、それを再開したい場合は、ここに状態を渡します。これを機能させるには、`return*state=true` を設定する必要があり、これにより `equation*search` が状態を返します。状態の第2要素は、名誉の殿堂を持つ通常の戻り値です。演算子やデータセットを変更することはできませんが、他のほとんどのオプションは変更可能であることに注意してください。
  * `return_state::Union{Bool, Nothing}=nothing`: ウォームスタートのために検索の状態を返すかどうか。デフォルトでは false です。
  * `loss_type::Type=Nothing`: 渡したデータとは異なる損失の型を使用したい場合は、ここに型を指定します。複素データ `::Complex{L}` を渡すと、損失の型は自動的に `L` に設定されます。
  * `verbosity`: デバッグステートメントを印刷するかどうか。
  * `logger::Union{AbstractSRLogger,Nothing}=nothing`: 検索の進行状況を記録するオプションのロガー。カスタムロガーをラップするために `SRLogger` を使用するか、ロギングを無効にするために `nothing` を渡すことができます。
  * `progress`: 進行状況バー出力を使用するかどうか。単一のターゲット出力にのみ利用可能です。
  * `X_units::Union{AbstractVector,Nothing}=nothing`: 次元制約に使用されるデータセットの単位。たとえば、`X_units=["kg", "m"]` の場合、最初の特徴はキログラムの単位を持ち、2 番目はメートルの単位を持ちます。
  * `y_units=nothing`: 次元制約に使用される出力の単位。`y` が行列の場合、これは単位のベクターであり、その場合、各要素は各出力特徴に対応します。

# 戻り値

  * `hallOfFame::HallOfFame`: 検索中に見られた最良の方程式。`hallOfFame.members` は `PopMember` オブジェクトの配列を提供し、これらのオブジェクトは `.tree` にツリー（方程式）を格納しています。損失は `.loss` に示されています。`PopMember` オブジェクトの配列は、`1` から `options.maxsize` までのサイズで列挙されます。
