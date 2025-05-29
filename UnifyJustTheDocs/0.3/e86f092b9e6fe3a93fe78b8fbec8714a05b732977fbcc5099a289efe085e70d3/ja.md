`just-the-docs` Jekyllテーマで使用するためにYAMLヘッダーを含むMarkdownファイルから`JTDPage`を作成します。

```julia
jtdpage(f; refpath)

```

`f`はMarkdownファイルへの明示的なフルページ（Julia `realpath()`）である必要があります。
