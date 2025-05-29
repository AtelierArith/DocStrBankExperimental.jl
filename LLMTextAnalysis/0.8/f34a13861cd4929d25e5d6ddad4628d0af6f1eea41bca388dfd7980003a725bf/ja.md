```
build_index(docs::Vector{<:AbstractString}; verbose::Bool = true,
index_id::Symbol = gensym("DocIndex"), aiembed_kwargs::NamedTuple = NamedTuple(),
keyword_kwargs::NamedTuple = NamedTuple(), kwargs...)
```

指定されたドキュメントのインデックスを構築し、それに埋め込みと抽出されたキーワードを含めます。

# 引数

  * `docs`: インデックスを作成するドキュメントのコレクション。大きなドキュメントが1つだけある場合は、`PromptingTools.split_by_length`を使用して小さなチャンクに分割することを検討してください。
  * `verbose`: INFO ロギングを有効にするフラグ。
  * `index_id`: ドキュメントインデックスの識別子。複数のインデックスがある場合に便利です。
  * `aiembed_kwargs`: `PromptingTools.aiembed`の追加引数。詳細については`?aiembed`を参照してください。
  * `keyword_kwargs`: キーワード抽出の追加引数。詳細については`?build_keywords`を参照してください。

# 戻り値

  * ドキュメント、埋め込み、キーワードなどに関する情報を含む`DocIndex`のインスタンス。

# 例

```julia
docs = ["First document text", "Second document text"]
index = build_index(docs)
```
