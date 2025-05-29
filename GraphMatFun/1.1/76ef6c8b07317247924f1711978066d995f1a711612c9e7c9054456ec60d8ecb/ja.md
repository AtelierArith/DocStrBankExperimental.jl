```
function export_compgraph(
        graph,
    fname;
    order = get_topo_order(graph)[1],
    fun = "",
    dom = "",
    err = "",
    genby = "",
    descr = "",
    user = splitdir(homedir())[end],
)
```

グラフをファイル `fname` に計算グラフ形式 (cgr) でエクスポートします。これらの kwargs は文字列またはファイルにコメントとして保存される値です。

  * グラフの `descr`
  * 近似する関数 `fun`
  * 近似するドメイン `dom`
  * このドメインの誤差 `err`
  * このファイルを生成したスクリプト `genby`
  * ファイルを作成したユーザー名 `user`

これらの kwarg はグラフの保存方法に影響を与えます：

  * `order` はグラフノードが保存される順序を指定します。

CGR形式：

各行はノード/操作に対応します。構文は matlab 互換ですが、[`gen_code`](@ref) はより高速な matlab コードを生成します。

さらに [`export_compgraph`](@ref) を参照してください。
