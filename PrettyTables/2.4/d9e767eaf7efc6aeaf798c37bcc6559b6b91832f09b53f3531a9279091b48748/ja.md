```
LatexHighlighter
```

LaTeXバックエンドを使用する際のテーブルのデフォルトハイライターを定義します。

# フィールド

  * `f::Function`: 要素 `(i, j)` がハイライトされるべき場合に `true` を返し、そうでない場合は `false` を返すシグネチャ `f(data, i, j)` を持つ関数。
  * `fd`: `data` が行列で、`(i, j)` がテーブル内の要素の位置、`str` が文字列に変換されたデータであるシグネチャ `f(data, i, j, str)::String` を持つ関数。この関数はセルに配置される文字列を返さなければなりません。

# 備考

この構造体は、2つのヘルパーを使用して構築できます：

```
LatexHighlighter(f::Function, envs::Union{String, Vector{String}})

LatexHighlighter(f::Function, fd::Function)
```

最初のものは、`envs` 内のすべてのLaTeX環境をハイライトされたテキストに再帰的に適用しますが、2番目のものはユーザーが関数 `fd` を指定することで希望の装飾を選択できるようにします。

したがって、例えば：

```
LatexHighlighter((data, i, j)->true, ["textbf", "small"])
```

は、テーブル内のすべてのセルを次の環境でラップします：

```
\textbf{\small{<Cell text>}}
```
