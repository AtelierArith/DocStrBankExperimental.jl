```
depgraph_image(
    pkgname;
    dir    = tempdir(),
    fmt    = :png,
    bg     = bg(fmt),
    open   = true,
    post   = true,
    kw...
)
```

指定されたパッケージの依存関係グラフを`dir`に画像としてレンダリングし、デフォルトの画像ビューアで開きます。外部プログラム '`dot`'（[graphviz.org](https://graphviz.org)を参照）が`PATH`に存在する必要があります。

`bg`: 画像の背景色。`fmt = :png`の場合はデフォルトで`:white`、それ以外の場合は`:transparent`です。

`fmt`は、`:svg`や`:png`など、dotがサポートする出力ファイル形式です。 `fmt`が`:svg`で、`post`が`true`（デフォルト）の場合、生成されたSVGファイルは、ライトモードとダークモードのCSSを追加するために後処理されます。

自動的に開かずに画像のみを作成するには、`open = false`を渡します。

他のキーワード引数は[`depgraph_as_dotstr`](@ref)に渡されます。
