```
create_simplicial_complex(labels::Vector{String},
                          simplices::Vector{Vector{Int}};
                          p::Int=2)
```

Lefschetz複体を単体複体から初期化します。複体は`p=0`の場合は有理数上で、`p>0`の場合は`GF(p)`上です。

ベクトル`labels`はすべての頂点に対するラベルを含み、`simplices`は単体複体を定義するために必要なすべての最高次元単体を含みます。各単体は`Int`のベクトルとして表され、エントリは頂点インデックスに対応します。

!!! warning
    すべてのラベルは同じ文字数である必要があることに注意してください!

