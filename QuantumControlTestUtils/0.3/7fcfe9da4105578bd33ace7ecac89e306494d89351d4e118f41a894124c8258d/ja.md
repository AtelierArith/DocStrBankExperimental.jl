既存のカバレッジデータのHTMLレポートを生成します。

```julia
generate_coverage_html(
    paths=["src", "ext"]; root=pwd(), covdir="coverage", genhtml="genhtml"
)
```

は、`root`内に`covdir`フォルダーを作成し、外部の`genhtml`プログラムを使用して、そのフォルダーにHTMLカバレッジレポートを書き込みます。
