```
read_emb(path::AbstractString)::WordEmbedding
```

この関数は、`.jld`および`.emb`形式のローカルバイナリ埋め込みテーブルファイルから単語埋め込みを読み込みます。これらのファイルは、名前が`"embedding"`の`WordEmbedding`オブジェクトを含むJuliaバイナリファイルです。
