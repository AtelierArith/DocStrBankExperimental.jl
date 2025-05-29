```
load_embeddings(EmbeddingSystem, [embedding_file|default_file_number])
load_embeddings(EmbeddingSystem{:lang}, [embedding_file|default_file_number])
```

埋め込みファイルから埋め込みを読み込みました。埋め込みは、埋め込みシステムによって指定されたタイプである必要があります。

`embedding file`が提供されていない場合、デフォルトの埋め込みファイルが使用されます。（必要に応じて自動的にインストールされます。）EmbeddingSystemsには言語タイプパラメータがあります。例えば`FastText_Text{:fr}`や`Word2Vec{:en}`のように、言語パラメータが指定されていない場合はデフォルトで英語になります。（多くの埋め込みフォーマットが英語でのみ事前学習されているため、NLP分野の状態が良くないことをお詫び申し上げます。）これを使用して、その言語に対して正しいデフォルトの埋め込みファイルがインストールされます。一部の言語や埋め込みシステムには、複数の可能なファイルがあります。例えば`language_files(FastText_Text{:de})`を使用して、それらのリストを確認できます。最初のものは名目上最も人気がありますが、別のものをデフォルトにしたい場合は、`default_file_num`を設定することで可能です。

### キーワード引数:

  * `max_vocab_size` 整数で、読み込む単語の最大数を指定します（ほとんどのフォーマットは頻度でソートされているため、最も一般的な単語を保持します）。デフォルトはすべての単語を保持することです。
  * `keep_words=Set()` 非空の単語のセットが提供される場合、そのリストの単語の埋め込みのみが読み込まれます。そうでない場合（デフォルト）はすべての単語が読み込まれます。

### `Embeddings`オブジェクトを返します。

これには2つのフィールドがあります。

  * `embeddings` は行列で、各列は単語の埋め込みです。
  * `vocab` は文字列のベクターで、`embeddings`の列に従って順序付けされており、`vocab`の最初の文字列は`embeddings`の最初の列に対応します。

単語から列のインデックスを取得するメソッドは含まれていません。これはコードで定義するのが簡単です（`vocab2ind(vocab)=Dict(word=>ii for (ii,word) in enumerate(vocab))`）、より一貫した方法でこれを行いたい場合は、[MLLabelUtils.jl](https://github.com/JuliaML/MLLabelUtils.jl)を使用するか、[InternedStrings.jl](https://github.com/JuliaString/InternedStrings.jl)の上により高速なDictソリューションを構築したいかもしれません。

```
