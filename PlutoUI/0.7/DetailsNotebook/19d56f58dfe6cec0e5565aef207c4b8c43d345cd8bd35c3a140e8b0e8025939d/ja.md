```julia
details(summary, contents; open::Bool=false)
```

折りたたみ可能な詳細開示要素（`<details>`）を作成します。

重要であるが冗長すぎるコンテンツや、常に表示する必要がない高度な変数を最初に隠すのに便利です。

# 引数

  * `summary::Any`: 詳細要素の常に表示される要約。
  * `contents::Any`: 詳細要素内にネストするアイテム。

# キーワード引数

  * `open::Bool=false`: 詳細要素が最初に開いているかどうか。

# 例

```julia
details("My summary", "Some contents")
```

```julia
details(
	"My summary",
	[
		"My first item",
		(@bind my_var Slider(1:10)),
		md"How are you feeling? $(@bind feeling Slider(1:10))",
	],
	open=true,
)
```

!!! warning "コレクション宣言における @bind に注意"
    `contents` 引数内で複数の変数を `@bind` したい場合は、`@bind` 式のコレクションを宣言することを検討してください。**各 `@bind` 式を括弧で囲む**か、上記の例のように `md` 文字列に埋め込んで、マクロ展開がコレクション宣言の解釈に影響を与えないようにしてください。


```julia
# この例はエラーを引き起こします
details(
	"My summary",
	[
		"My first item",
		@bind my_var Slider(1:10),
	]
)
```
