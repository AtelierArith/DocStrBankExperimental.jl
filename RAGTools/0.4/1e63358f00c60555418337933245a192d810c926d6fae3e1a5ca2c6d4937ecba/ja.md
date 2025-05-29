```
get_chunks(chunker::AbstractChunker,
	files_or_docs::Vector{<:AbstractString};
	sources::AbstractVector{<:AbstractString} = files_or_docs,
	verbose::Bool = true,
	separators = ["\n\n", ". ", "\n", " "], max_length::Int = 256)
```

提供された `files_or_docs` を最大長 `max_length` のチャンクに分割します（提供された `separators` で可能な場合）。

2つの動作モードをサポートしています：

  * `chunker = FileChunker()`: この関数は `files_or_docs` の各ファイルを開き、その内容を読み取ります。
  * `chunker = TextChunker()`: この関数は `files_or_docs` がチャンク化される文字列のベクターであると仮定し、対応する `sources` を提供する必要があります。

# 引数

  * `files_or_docs`: 有効なファイルパスまたはチャンク化される文字列ドキュメントのベクター。
  * `separators`: 各ファイルのテキストをチャンクに分割するために使用される区切り文字列のリスト。デフォルトは `[\n\n", ". ", "\n", " "]` です。詳細については `recursive_splitter` を参照してください。
  * `max_length`: 各チャンクの最大長（提供された区切り文字で可能な場合）。デフォルトは 256 です。
  * `sources`: 各チャンクのソースを示す文字列のベクター。デフォルトは `files_or_docs` と等しい（`reader=:files` の場合）。
