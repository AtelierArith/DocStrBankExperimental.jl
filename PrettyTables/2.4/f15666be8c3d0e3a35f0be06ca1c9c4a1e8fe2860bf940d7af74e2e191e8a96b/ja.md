```
struct MarkdownHighlighter
```

マークダウンバックエンドを使用する際のテーブルのデフォルトハイライターを定義します。

# フィールド

  * `f::Function`: 要素 `(i, j)` が `data` でハイライトされるべき場合に `true` を返す必要がある、シグネチャ `f(data, i, j)` を持つ関数。
  * `fd::Function`: `h` がハイライターであるシグネチャ `fd(h, data, i, j)` を持つ関数。この関数は、ハイライトされるべきセルに適用される `MarkdownDecoration` を返さなければなりません。
  * `decoration::MarkdownDecoration`: デフォルトの `fd` が使用される場合にハイライトされるセルに適用される `MarkdownDecoration`。

# 備考

この構造体は、2つのヘルパーを使用して構築できます：

```
MarkdownHighlighter(f::Function, decoration::MarkdownDecoration)

MarkdownHighlighter(f::Function, fd::Function)
```

最初のものは、`decoration` で指定されたハイライトされるセルに固定の装飾を適用しますが、2番目のものは、ユーザーが関数 `fd` を指定することで希望の装飾を選択できるようにします。
