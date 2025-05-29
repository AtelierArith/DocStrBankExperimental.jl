```
HtmlHighlighter
```

HTMLバックエンドを使用する際のテーブルのデフォルトハイライターを定義します。

# フィールド

  * `f::Function`: `f(data,i,j)`というシグネチャを持つ関数で、`data`の要素`(i,j)`をハイライトする必要がある場合は`true`を、そうでない場合は`false`を返す必要があります。
  * `fd::Function`: `f(h,data,i,j)`というシグネチャを持つ関数で、ここで`h`はハイライターです。この関数は、ハイライトする必要があるセルに適用される`HtmlDecoration`を返さなければなりません。
  * `decoration::HtmlDecoration`: デフォルトの`fd`が使用される場合にハイライトされたセルに適用される`HtmlDecoration`です。

# 備考

この構造体は、2つのヘルパーを使用して構築できます：

```
HtmlHighlighter(f::Function, decoration::HtmlDecoration)

HtmlHighlighter(f::Function, fd::Function)
```

最初のものは、`decoration`で指定されたハイライトされたセルに固定の装飾を適用しますが、2番目のものは、ユーザーが`fd`関数を指定することで希望の装飾を選択できるようにします。
