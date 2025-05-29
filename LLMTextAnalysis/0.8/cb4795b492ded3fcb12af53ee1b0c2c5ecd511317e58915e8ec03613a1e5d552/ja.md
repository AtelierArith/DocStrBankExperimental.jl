```
train_spectrum(index::AbstractDocumentIndex,
    spectrum::Tuple{String, String};
    num_samples::Int = 100, verbose::Bool = true,
    rewriter_template::Symbol = :StatementRewriter,
    lambda::Real = 1e-5,
    aigenerate_kwargs::NamedTuple = NamedTuple(),
    aiembed_kwargs::NamedTuple = NamedTuple(),)
```

スペクトルをトレーニングします。つまり、極端に対立する概念の二面軸です。

私たちは、選択した二つの概念を表す埋め込み空間の「方向」を効果的に特定します。

実際には、`index`から`num_samples`の文書を取得し、指定されたレンズ（スペクトルの端）を通してそれらを再構成し、これらの再構成された文書を埋め込み、最後に文書をスペクトルに従って分類するためのロジスティック回帰モデルをトレーニングします。

関連情報: `train!`, `train_concept`, `score`

# 引数

  * `index::AbstractDocumentIndex`: 分析する文書を含むインデックス。このインデックスは、`build_index`を使用して以前に構築されている必要があります。
  * `spectrum::Tuple{String, String}`: 文書が再構成される二つのレンズを表す文字列のペア。例えば、("optimistic", "pessimistic")はスペクトルの一例です。
  * `num_samples::Int` (オプション): トレーニングのためにインデックスからサンプリングする文書の数。デフォルトは100です。
  * `verbose::Bool` (オプション): `true`の場合、プロセス中に詳細なログを出力します。デフォルトは`true`です。
  * `rewriter_template::Symbol` (オプション): ステートメントを再構成するために使用されるテンプレート。デフォルトは`:StatementRewriter`です。
  * `lambda::Real` (オプション): ロジスティック回帰の正則化パラメータ。デフォルトは1e-5です。交差検証の精度が低すぎる場合は調整してください。
  * `aigenerate_kwargs::NamedTuple` (オプション): `aigenerate`関数の追加引数。詳細については`?aigenerate`を参照してください。
  * `aiembed_kwargs::NamedTuple` (オプション): `aiembed`関数の追加引数。詳細については`?aiembed`を参照してください。

# 戻り値

  * トレーニングされたモデル（`coeffs`）を含む`TrainedSpectrum`オブジェクトと、再構成された文書（`docs`）や埋め込み（`embeddings`）などの関連情報。

# 例

```julia
# 既存の文書インデックスが`index`であると仮定
my_spectrum = ("pessimistic", "optimistic")
spectrum = train_spectrum(index, my_spectrum)
```

スペクトル2（この例では「optimistic」）の最高得点の文書上位5件を表示します：

```julia
scores = score(index, spectrum)
index.docs[first(sortperm(scores, rev = true), 5)]

# rev=falseを使用してスペクトル1（反対側）の最高得点の文書を取得
```

AI生成および埋め込み関数に追加の引数を渡すことで、分析をカスタマイズできます。例えば、生成に使用するモデルやサンプル数を指定できます：

```julia
spectrum = train_spectrum(index,
    ("forward-looking", "dwelling in the past");
    num_samples = 50, aigenerate_kwargs = (; model = "gpt3t"))
```

この関数は、大規模な言語モデルを利用してテキストを再構成および分析し、指定されたスペクトルに基づいて洞察を提供します。出力には埋め込みと、新しい文書をこのスペクトルに投影して分析するためのモデルが含まれます。

トラブルシューティングのために、モデルを手動でフィットさせ、精度を確認できます：

```julia
X = spectrum.embeddings'
# 前半はスペクトル1、後半はスペクトル2
y = vcat(-1ones(length(spectrum.source_doc_ids)), ones(length(spectrum.source_doc_ids))) .|>
    Int
accuracy = cross_validate_accuracy(X, y; k = 4, lambda = 1e-8)
```

または、ソース文書と再構成された文書を探索できます：

```julia
# ソース文書
index.docs[spectrum.source_doc_ids]

# 再構成された文書
spectrum.docs
```
