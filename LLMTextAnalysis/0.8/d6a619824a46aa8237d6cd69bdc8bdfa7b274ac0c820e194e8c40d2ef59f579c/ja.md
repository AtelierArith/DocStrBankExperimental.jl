```
build_clusters!(index::AbstractDocumentIndex, assignments::Vector{Int};
    topic_level::AbstractString = "",
    labels::Union{Vector{String}, Nothing} = nothing,
    verbose::Bool = true, add_label::Bool = false, add_summary::Bool = false,
    labeler_kwargs::NamedTuple = NamedTuple())
```

提供された `labels` と `assignments`（各ドキュメント `index` が属するトピックのベクトル）に基づいてカスタムトピックを構築します。

# 引数

  * `index`: ドキュメントインデックス。
  * `assignments`: 各ドキュメントのトピック割り当てのベクトル（例: `[2,3]` -> 最初のドキュメントはトピック2に割り当てられ、2番目のドキュメントはトピック3に割り当てられます）。
  * `topic_level`: 作成するトピックレベルの名前。指定しない場合は自動生成されます（例: `Custom_1`）。
  * `labels`: 知っている場合は各トピックのラベルのベクトル。そうでない場合は、`add_label=true`を設定すると生成できます。
  * `verbose`: INFOロギングを有効にするフラグ。
  * `add_label`: トピックラベリングを有効にするフラグ、つまり、LLMを呼び出してトピックラベルを生成します。
  * `add_summary`: トピック要約を有効にするフラグ、つまり、LLMを呼び出してトピック要約を生成します。
  * `labeler_kwargs`: LLMラベラーに渡すキーワード引数。利用可能な引数の詳細については `?build_topic` を参照してください。

# 例

2つのクラスターを持つシンプルな例：

```julia
assignments = ones(Int,length(index.docs)) # 各ドキュメントが属するクラスター
assignments[1:5] = 2 # 最初の5つのドキュメントはクラスター2に属します

build_clusters!(index, assignments; topic_level="MyDualCluster", labels = ["Cluster 1", "Cluster 2"])
```
