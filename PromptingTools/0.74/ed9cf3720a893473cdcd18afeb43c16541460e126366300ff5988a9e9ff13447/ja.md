```
recursive_splitter(text::AbstractString, separators::Vector{String}; max_length::Int=35000) -> Vector{String}
```

与えられた文字列 `text` を一連の区切り文字を使用して再帰的にチャンクに分割します。各チャンクは `max_length` の最大長を持ちます（提供された `separators` に基づいて達成可能な場合）。この関数は、大きな文書やテキストを処理しやすい小さなセグメントに分割するのに役立ちます。特に、コンテキストウィンドウが限られているモデルやシステムに対して有用です。

以前は `split_by_length` として知られていました。

これは Langchain の [`RecursiveCharacterTextSplitter`](https://python.langchain.com/docs/modules/data_connection/document_transformers/recursive_text_splitter) に似ています。同じ動作を実現するには、`separators=["\n\n", "\n", " ", ""]` を使用してください。

# 引数

  * `text::AbstractString`: 分割するテキスト。
  * `separators::Vector{String}`: テキストを分割するために使用される区切り文字の順序付きリスト。この関数は、これらの区切り文字を反復的に適用してテキストを分割します。`["\n\n", ". ", "\n", " "]` の使用を推奨します。
  * `max_length::Int`: 各チャンクの最大長。デフォルトは35,000文字です。この長さは、分割の各反復後に考慮され、チャンクが指定された制約内に収まるようにします。

# 戻り値

`Vector{String}`: 各文字列が元のテキストのチャンクであり、`max_length` 以下のサイズの文字列のベクター。

# 使用のヒント

  * 私は、テキストの構造を保持するために、改行文字（`"\n"`）で分割する前に文（`". "`）で分割することを好みます。
  * `separators=["\n"," ",""]` と `separators=["\n"," "]` の違いは何ですか？前者は文字レベル（`""`）まで分割するため、常に `max_length` を達成しますが、単語を分割します（コンテキストには悪影響！）。私は、単語を分割せずに少し小さめの `max_length` を設定することを好みます。

# 仕組み

  * 関数は、提供された順序で各区切り文字を使用してテキストを反復的に処理します。次に、各チャンクの長さを測定し、`max_length` を超える場合はさらに分割します。チャンクが「十分に短い」場合、次の区切り文字は適用されません。
  * 各チャンクは、可能な限り `max_length` に近いです（分割できない場合、例えば、分割子が「大きすぎる」/十分でない場合を除く）。
  * `text` が空の場合、関数は空の配列を返します。
  * 分割後、区切り文字はテキストチャンクに再追加され、元のテキストの構造をできるだけ保持します。必要ない場合は `strip` を適用してください。
  * 関数は、単一の区切り文字の対応物と区別するために、2番目の引数として `separators` を提供します。

# 例

複数の区切り文字を使用してテキストを分割する：

```julia
text = "Paragraph 1\n\nParagraph 2. Sentence 1. Sentence 2.\nParagraph 3"
separators = ["\n\n", ". ", "\n"] # 段落、文、改行で分割（単語では分割しない）
chunks = recursive_splitter(text, separators, max_length=20)
```

複数の区切り文字を使用してテキストを分割する - 単語で分割する場合：

```julia
text = "Paragraph 1\n\nParagraph 2. Sentence 1. Sentence 2.\nParagraph 3"
separators = ["\n\n", ". ", "\n", " "] # 段落、文、改行、単語で分割
chunks = recursive_splitter(text, separators, max_length=10)
```

単一の区切り文字を使用する：

```julia
text = "Hello,World," ^ 2900  # 長さ 34900 文字
chunks = recursive_splitter(text, [","], max_length=10000)
```

Langchain の `RecursiveCharacterTextSplitter` と同じ動作を実現するには、`separators=["\n\n", "\n", " ", ""]` を使用してください。

```julia
text = "Paragraph 1\n\nParagraph 2. Sentence 1. Sentence 2.\nParagraph 3"
separators = ["\n\n", "\n", " ", ""]
chunks = recursive_splitter(text, separators, max_length=10)

```
