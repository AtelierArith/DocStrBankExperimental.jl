```
PageNode(input; visible, collapsed)
PageNode(this_page, children; visible, collapsed)
```

`PageNode`オブジェクトを作成します。これは、いくつかの子を持つことができます。

`input`は、`Documenter.makedocs`で`pages`が受け入れる任意のものであり、例えば文字列、文字列のペア、文字列またはペアのベクトル、またはそれらの任意の組み合わせです。

2引数のコンストラクタで、トップレベルページとその子の詳細を別々に指定することもできます。

## 例

```julia
PageNode("index.md")
```

```julia
PageNode("Home" => "index.md")
```

```julia
PageNode(["index.md", "gallery.md"])
```
