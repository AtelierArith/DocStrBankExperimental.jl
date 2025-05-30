```
read_indexed_emb(path::AbstractString)::WordEmbedding
```

この関数は、`.jld2`および`.iem`形式のローカルバイナリ埋め込みテーブルファイルからインデックス付き単語埋め込みを読み込みます。これらのファイルは、名前が`"embedding"`の`IndexedWordEmbedding`オブジェクトを含むJuliaバイナリファイルです。
