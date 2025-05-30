```
to_documenter(p::P; id, version)
```

プロットオブジェクト `p` を受け取り、Documenter.jl から生成されたページ内で HTML として表示可能な出力を返します。この関数は、Documenter.jl の `@example` ブロック内で最後のステートメント/コマンドとして呼び出された場合に正しく動作します。動作を確認するには、パッケージの [ドキュメント](https://disberd.github.io/PlotlyDocumenter.jl) をチェックしてください。

出力として返されるオブジェクトは、`text/html` として表示されると、ドキュメントページ内で直接操作可能な plotly プロットを生成します。

このパッケージは、`P` として以下のタイプをサポートしています：

  * PlotlyBase の `Plot`
  * PlotlyBase の `SyncPlot`
  * PlotlyLight の `Plot`

# キーワード引数

  * `id`: プロットを含む div に与えられる id。デフォルトは 10 の英数字からなるランダムな文字列です。
  * `version`: 使用する plotly.js のバージョン。デフォルトはバージョン 2.24.2 ですが、`version` を文字列として提供することで上書きできます。デフォルトバージョンを変更するには、未エクスポートの `change_default_plotly_version` 関数を使用します。
  * `classes`: プロットを含む div に割り当てるクラスを表す文字列のベクター。デフォルトは空のベクターです。
  * `style`: プロットオブジェクトにインラインで適用されるスタイルのリストを含むオブジェクト。デフォルトは空の NTuple です。[HypertextLiteral](https://juliapluto.github.io/HypertextLiteral.jl/stable/attribute/#Pairs-and-Dictionaries) の構文をサポートしています。

# 注意事項

  * このパッケージは、プロットパッケージを再エクスポートしないため、必要なプロットパッケージは独立してスコープに取り込む必要があります。
  * このパッケージは現在、CDN から plotly ライブラリを取得することのみをサポートしているため、PlotlyLight などによってサポートされているローカルバージョンの Plotly はサポートしていません。
