HTML文字列を注釈付き文`sa`のために、トークン注釈のベクトルからデータを使用して作成します。`sov`と`vucolor`のブールフラグは、主語-目的語-動詞のハイライトと動詞単位による色分けのためのCSS追加を引き起こします。

```julia
htmltext(
    sa,
    tknannotations;
    sov,
    vucolor,
    colors,
    syntaxtips,
    connectorids
)

```
