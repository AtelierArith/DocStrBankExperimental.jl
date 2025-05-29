```
build_clusters!(index::AbstractDocumentIndex; k::Union{Int, Nothing} = nothing,
    h::Union{Float64, Nothing} = nothing,
    verbose::Bool = true, add_label::Bool = true, add_summary::Bool = false,
    labeler_kwargs::NamedTuple = NamedTuple(),
    cluster_kwargs...)
```

ドキュメントインデックスに対して自動クラスタリングを実行し、異なるレベルでトピックを構築します。

# 引数

  * `index`: ドキュメントインデックス。
  * `k`: 切り取るクラスタの数。
  * `h`: デンドログラムを切り取る高さ。詳細については `?Clustering.hclust` を参照してください。
  * `verbose`: INFO ロギングを有効にするフラグ。
  * `add_label`: トピックラベリングを有効にするフラグ、つまり、LLMを呼び出してトピックラベルを生成します。
  * `add_summary`: トピック要約を有効にするフラグ、つまり、LLMを呼び出してトピック要約を生成します。
  * `labeler_kwargs`: LLMラベラーに渡すキーワード引数。利用可能な引数の詳細については `?build_topic` を参照してください。
  * `cluster_kwargs`: 残りのすべての引数は `Clustering.hclust` に渡されます。利用可能な引数の詳細については `?Clustering.hclust` を参照してください。

# 戻り値

  * クラスタリング情報とトピックメタデータを含む更新されたインデックス。

# 例

```julia
index = build_index(["Doc 1", "Doc 2"])
clustered_index = build_clusters!(index, k=2)
```
