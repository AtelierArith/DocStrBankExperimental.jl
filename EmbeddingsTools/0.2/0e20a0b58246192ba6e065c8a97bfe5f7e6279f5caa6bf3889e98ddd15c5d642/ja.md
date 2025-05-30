```
read_embedding(
    path::AbstractString;
    delim::AbstractChar=' ',
    max_vocab_size::Union{Int,Nothing}=nothing,
    keep_words::Union{Vector{String},Nothing}=nothing
)::WordEmbedding
```

関数 `read_embedding()` は、従来の方法で埋め込みファイルを読み込むために使用されます。これは、CSV.jlを使用して `WordEmbedding` オブジェクトを作成します。この関数は、ローカルの埋め込みベクトルへのパスを引数として受け取り、2つのオプションのキーワード引数 `max_vocab_size` と `keep_words` を持っています。

`max_vocab_size` が指定されている場合、関数はベクトルのサイズをその数に制限します。`keep_words` ベクトルが提供されている場合、それらの単語のみを保持します。`keep_words` に含まれる単語が見つからない場合、関数はその単語に対してゼロベクトルを返します。

ファイルがJuliaバイナリファイル内の `WordEmbedding` オブジェクト（拡張子 `.jld` または特定の形式 `.emb` または `.wem`）である場合、全体の埋め込みがロードされ、キーワード引数は適用されません。また、バイナリファイルに対して直接 `read_emb()` 関数を使用することもできます。事前に保存されたインデックス付き埋め込みについては、現在 `read_indexed_emb()` が唯一のオプションです。

# 注意事項

`max_vocab_size` を 45k 以上に設定すると、関数のパフォーマンスが `limit(read_embedding(path), max_vocab_size)` と比較して低下する可能性があることに注意してください。これは、このパラメータを使用すると、CSV.jlのジョブが単一スレッドに制限されるためです。ただし、`max_vocab_size` を使用すると、ファイル全体を読み込むよりもメモリの割り当てが少なくなります。

さらに、1kの選択された単語を持つ `keep_words` を使用すると、`subspace(index(read_embedding(path)), keep_words)` と比較して、かなり遅くなるものの、メモリ効率は向上します。10kの選択された単語を読み込むには、5秒以上かかる場合があります。
