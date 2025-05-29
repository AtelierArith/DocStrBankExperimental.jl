```
create_simplicial_complex(labels::Vector{String},
                          simplices::Vector{Vector{String}};
                          p::Int=2)
```

シンプレクシャル複体からレフシェッツ複体を初期化します。複体は `p=0` の場合は有理数上で、`p>0` の場合は `GF(p)` 上です。

ベクトル `labels` はすべての頂点のラベルを含み、`simplices` はシンプレクシャル複体を定義するために必要なすべての最高次元シンプレクスを含みます。
