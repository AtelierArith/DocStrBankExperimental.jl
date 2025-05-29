```
train_classifier(index::AbstractDocumentIndex,
    labels::AbstractVector{<:AbstractString};
    docs_ids::AbstractVector{<:Integer} = Int[],
    docs_labels::AbstractVector{<:Integer} = Int[],
    labels_description::Union{Nothing, AbstractVector{<:AbstractString}} = nothing,
    num_samples::Int = 5, verbose::Bool = true,
    writer_template::Symbol = :TextWriterFromLabel,
    lambda::Real = 1e-3,
    aigenerate_kwargs::NamedTuple = NamedTuple(),
    aiembed_kwargs::NamedTuple = NamedTuple())
```

`labels`（`labels_description`で詳細に説明）に基づいて、各文書をいくつかの特定のトピックの1つに分類するモデルをトレーニングします。

ユーザーがインデックスから文書とそれに対応するラベル（それぞれ`docs_ids`と`docs_labels`）を提供した場合、モデルはそれらの文書でトレーニングされます。バランスの取れたデータセットを目指し（すべての`labels`が存在する必要があります）、各ラベルごとに最低5つの文書（理想的にはそれ以上）を用意してください。

そうでない場合、最初に`labels`の各ラベルに対して`num_samples`の合成文書を生成します。つまり、合計で`num_samples x length(labels)`の生成された文書があります。`labels_description`が提供されている場合、これらの説明はAIモデルに提供され、各ラベルに対してより多様で関連性のある文書を生成するために使用されます（単語ラベルよりも情報量が多いです）。

内部では、文書の埋め込みの上にマルチラベル分類器をトレーニングします。

結果として得られるスコアは、各文書と各ラベルの確率の行列になります。スコアの次元：`num_documents x num_labels`、つまり、位置[1,3]は、最初の文書が3番目のラベル/クラスに対応する確率に相当します。各文書に最適なラベルを選択するには、`argmax(scores, dims=2)`を使用できます。

関連情報：`score`、`train!`、`train_spectrum`、`train_concept`

# 引数

  * `index::AbstractDocumentIndex`: 分析する文書を含むインデックス。
  * `labels::AbstractVector{<:AbstractString}`: 分類器のトレーニングに使用されるラベルのベクター（文書はこれらのラベルの1つに割り当てられます）。
  * `docs_ids::AbstractVector{<:Integer}`（オプション）：トレーニングに使用する`index`内の文書のID。デフォルトは空のベクターで、合成文書が生成されます。
  * `docs_labels::AbstractVector{<:Integer}`（オプション）：`docs_ids`内の文書に対応するラベル。デフォルトは空のベクターです。
  * `labels_description::Union{Nothing, AbstractVector{<:AbstractString}}`（オプション）：各ラベルの説明のベクター。提供されると、各ラベルに対してより多様で関連性のある文書を生成するために使用されます。デフォルトは`nothing`です。
  * `num_samples::Int`（オプション）：`labels`の各ラベルに対して生成する文書の数。デフォルトは5です。
  * `verbose::Bool`（オプション）：`true`の場合、プロセス中に詳細なログを出力します。デフォルトは`true`です。
  * `writer_template::Symbol`（オプション）：合成文書を書くために使用されるテンプレート。デフォルトは`:TextWriterFromLabel`です。
  * `lambda::Real`（オプション）：ロジスティック回帰の正則化パラメータ。デフォルトは1e-3です。
  * `aigenerate_kwargs::NamedTuple`（オプション）：`aigenerate`関数の追加引数。詳細については`?aigenerate`を参照してください。
  * `aiembed_kwargs::NamedTuple`（オプション）：`aiembed`関数の追加引数。詳細については`?aiembed`を参照してください。

# 戻り値

  * トレーニングされたモデルを含む`TrainedClassifier`オブジェクトと、生成された文書（`docs`）、埋め込み（`embeddings`）、モデル係数（`coeffs`）などの関連情報。

# 例

インデックス内のラベル付き文書のセットに対して分類器を作成します（つまり、いくつかの文書のラベルがわかっています）：

```julia
# `index`が既存の文書インデックスであると仮定します

# トピックの名前と対応するラベル付き文書を提供します
labels = ["交通状況の改善", "税金と公共資金",
    "安全とコミュニティ", "その他"]

# いくつかの文書にラベルを付けたとしましょう - 理想的には、各ラベルに対して5〜10の例を持っているべきです
docs_ids = [1, 2674, 4, 17, 23, 69, 2669, 6]
docs_labels = [1, 1, 2, 2, 3, 3, 4, 4] # 各文書が属するトピック

# 分類器をトレーニングします
cls = train_classifier(index, labels; docs_ids, docs_labels)

# インデックス内の文書のスコアを取得します
score(index, cls) # または cls(index)
```

ラベル付き文書がない場合は、AIモデルにいくつかの潜在的な例を生成するように依頼できます（各トピック/ラベルごとに`num_samples`）。生成された文書の質を向上させるためにラベルの説明を提供することが役立ちます：

```julia
# `index`が既存の文書インデックスであると仮定します

labels_description = [
    "インフラ、交通状況の改善および関連する内容に関する調査回答",
    "税金を減らし、コミュニティにもっとお金を渡すこと",
    "ホームレス、一般的な安全およびコミュニティ関連のトピックに関する調査回答",
    "環境、教育、ガバナンスなどのその他のトピック"]

# 分類器をトレーニングします - 20の文書例が生成されます（各ラベルごとに5つの文書 x 4ラベル）
cls = train_classifier(index, labels; labels_description, num_samples=5)

# すべての文書のスコアを取得します
scores = score(index, cls)

# インデックス内のすべての文書のラベルを取得します
best_labels = score(index, cls; return_labels = true)
```
