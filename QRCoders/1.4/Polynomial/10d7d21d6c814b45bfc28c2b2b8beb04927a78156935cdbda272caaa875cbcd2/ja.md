```
generator_matrix(msglen::Int, necwords::Int)
```

サイズ `(msglen + necwords, msglen)` の生成行列を作成します。

生成行列 G は次の形式です

```
[ * ]
[ I ]
```

ここで `I` はサイズ `msglen` の単位行列であり、`*` は余り多項式によって計算されます。

生成行列の逆バージョンを使用していることに注意してください。すなわち、係数は逆順に格納されます。例えば、a*0, ..., a*n のように。

この意味で、依然として G⋅x = c が成り立ちます。ここで x はメッセージ多項式であり、c は受信多項式です。

通常の生成行列を得るには、180度回転させるだけです。すなわち、@view(G[end:-1:1, end:-1:1])
