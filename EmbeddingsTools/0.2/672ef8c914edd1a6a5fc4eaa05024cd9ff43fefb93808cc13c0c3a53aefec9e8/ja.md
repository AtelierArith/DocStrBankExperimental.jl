```
read_vec(path::AbstractString; delim::AbstractChar=' ')::WordEmbedding
```

関数 `read_vec()` は、指定された `path` のテキストファイル (.txt, .vec など) からローカル埋め込み行列を読み込むために使用されます。これは、CSV.jl パッケージを使用して `WordEmbedding` オブジェクトを作成します。テキストファイルに使用される区切り文字は、`delim` パラメータを使用して設定できます。この関数は `read_embedding()` の簡略版であり、常に埋め込みテーブル全体を読み込むため、ロジックがより簡潔になります。
