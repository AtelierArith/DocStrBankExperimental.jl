```julia
to_html_content(expr)
```

DSL式から`HTMLContent`を作成します。`divv`があなたのDSLに基づいて`expr`からHTMLの文字列を生成することを前提としています。

## 引数

  * `expr`: HTMLに変換されるDSL式。

## 戻り値

  * 生成されたHTML文字列を含む`HTMLContent`のインスタンス。

## 例

```julia
html_expr = divv(
    head(
        title("Hello, World!")
    ),
    body(
        h1("Hello, World!")
    )
)
html_content = to_html_content(html_expr)
```
