```
cardtheme(theme = "grid";
          root = "<current-directory>",
          src = "src",
          destination = "democards") -> templates, stylesheet_path
```

指定されたテーマに対して、テンプレートとスタイルシートへのパスを返します。

`root` と `destination` は `makedemos` に渡されたのと同じ値である必要があります。

利用可能なテーマは次のとおりです：

  * "bulmagrid"
  * "bokehlist"
  * "grid"
  * "list"
  * "nocoverlist"
  * "transitiongrid"
