```
struct Highlighter
```

テキストバックエンドを使用する際のテーブルのデフォルトハイライターを定義します。

# フィールド

  * `f::Function`: 要素 `(i,j)` がハイライトされるべき場合に `true` を返す関数 `f(data, i, j)` のシグネチャ。
  * `fd::Function`: `h` がハイライターである関数 `f(h, data, i, j)` のシグネチャ。この関数は、ハイライトされるべきセルに適用される `Crayon` を返さなければなりません。
  * `crayon::Crayon`: デフォルトの `fd` が使用される場合にハイライトされるセルに適用される `Crayon`。

# 備考

この構造体は、3つのヘルパーを使用して構築できます：

```
Highlighter(f::Function; kwargs...)
```

ここでは、`kwargs` のキーワードを使用して `Crayon` を構築し、ハイライトされるセルに適用します。

```
Highlighter(f::Function, crayon::Crayon)
```

ここでは、ハイライトされるセルに `crayon` を適用します。

```
Highlighter(f::Function, fd::Function)
```

ここでは、ハイライトされるセルに関数 `fd` が返す `Crayon` を適用します。
