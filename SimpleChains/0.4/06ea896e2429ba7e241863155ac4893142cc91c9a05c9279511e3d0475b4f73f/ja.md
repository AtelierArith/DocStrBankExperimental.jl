```
Conv(activation, dims::Tuple{Vararg{Integer}}, outputdim::Integer)
```

`dims` を使って畳み込みを行い、`outputdim` 出力チャネルにマッピングし、その後バイアス（各 `outputdim` ごとに1つ）を加え、要素ごとに `activation` を適用します。

例えば、`Conv(relu, (5, 5), 16)` は `5 × 5` の畳み込みを行い、入力チャネルを16の出力チャネルにマッピングし、その後バイアスを加え、`relu` を適用します。

(Xavier) グロロット一様分布を使用して重みをランダムに初期化します。バイアスはゼロ初期化されています。
