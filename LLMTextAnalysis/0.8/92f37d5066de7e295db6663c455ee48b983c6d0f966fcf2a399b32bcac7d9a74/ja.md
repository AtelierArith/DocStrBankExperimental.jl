```
train_concept(index::AbstractDocumentIndex,
              concept::String;
              num_samples::Int = 100, verbose::Bool = true,
              rewriter_template::Symbol = :StatementRewriter,
              lambda::Real = 1e-3, negatives_samples::Int = 1,
              aigenerate_kwargs::NamedTuple = NamedTuple(),
              aiembed_kwargs::NamedTuple = NamedTuple(),)
```

特定の概念（文字列 `concept` で定義）を `index` からの `num_samples` ドキュメントに基づいて識別し、スコアを付けるモデルをトレーニングします。

私たちは、この概念を表す埋め込み空間の「方向」を効果的に特定し、それに対してドキュメントをスコアリングできるモデルを開発します。

この関数は、ドキュメント内の存在、強さ、または現れ方を測定するために、スペクトル（`train_spectrum` を参照）ではなく、単一の概念に焦点を当てています。

関連情報: `train_spectrum`, `train!`, `score`

# 引数

  * `index::AbstractDocumentIndex`: 分析するドキュメントを含むインデックス。
  * `concept::String`: ドキュメント内で分析する概念。
  * `num_samples::Int`（オプション）: トレーニングのためにインデックスからサンプリングするドキュメントの数。デフォルトは100。
  * `verbose::Bool`（オプション）: `true` の場合、プロセス中に詳細なログを出力します。デフォルトは `true`。
  * `rewriter_template::Symbol`（オプション）: ステートメントを再構成するために使用されるテンプレート。デフォルトは `:StatementRewriter`。
  * `lambda::Real`（オプション）: ロジスティック回帰の正則化パラメータ。デフォルトは1e-3。
  * `negatives_samples::Int`（オプション）: 各ポジティブサンプルのトレーニングに使用するネガティブ例の数。デフォルトは1。
  * `aigenerate_kwargs::NamedTuple`（オプション）: `aigenerate` 関数の追加引数。詳細は `?aigenerate` を参照。
  * `aiembed_kwargs::NamedTuple`（オプション）: `aiembed` 関数の追加引数。詳細は `?aiembed` を参照。

# 戻り値

  * トレーニングされたモデルを含む `TrainedConcept` オブジェクトと、再構成されたドキュメント（`docs`）、埋め込み（`embeddings`）、およびモデル係数（`coeffs`）などの関連情報。

# 例

```julia
# `index` が既存のドキュメントインデックスであると仮定
my_concept = "sustainability"
concept_model = train_concept(index, my_concept)
```

概念に対してスコアが最も高い上位5つのドキュメントを表示します：

```julia
scores = score(index, concept)
index.docs[first(sortperm(scores, rev = true), 5)]
```

AI生成および埋め込み関数に追加の引数を渡すことで、トレーニングをカスタマイズできます。たとえば、生成に使用するモデルや使用するサンプル数を指定できます：

```julia
concept = train_concept(index,
    "action-oriented";
    num_samples = 50,
    aigenerate_kwargs = (; model = "gpt3t"))
```

この関数は、大規模な言語モデルを活用して、ドキュメントコーパス内の特定の概念の存在と変動を抽出および分析します。テーマ研究、感情分析、または大規模なテキストコレクションにおけるトレンドの特定に特に役立ちます。

さらなる分析のために、再構成されたドキュメントとその埋め込みを検査できます：

```julia
# 概念に関連する再構成されたドキュメント
concept_model.docs

# 再構成されたドキュメントの埋め込み
concept_model.embeddings
```
