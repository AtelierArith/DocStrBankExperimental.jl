```
writemultinewick(nets, file_name; append=false)
writemultinewick(nets, IO)
```

ネットワークの配列を括弧付き拡張ニューウィック形式で書き込みます。1つのネットワークにつき1行です。ファイルに追加するには、オプション `append=true` を使用します。そうでなければ、デフォルトでは新しいファイルを作成するか、既に存在する場合は上書きします。各ネットワークは `writenewick` で書き込まれます。

# 例

```julia
julia> net = [readnewick("(D,((A,(B)#H7:::0.864):2.069,(F,E):3.423):0.265,(C,#H7:::0.1361111):10);"),
              readnewick("(A,(B,C));"),readnewick("(E,F);"),readnewick("(G,H,F);")];

julia> writemultinewick(net, "fournets.net") # ファイル "fournets.net" に書き込む（上書き）
julia> writemultinewick(net, "fournets.net", append=true) # このファイルに追加
julia> writemultinewick(net, stdout)         # 画面（標準出力）に書き込む
(D,((A,(B)#H7:::0.864):2.069,(F,E):3.423):0.265,(C,#H7:::0.1361111):10.0);
(A,(B,C));
(E,F);
(G,H,F);
```
