文字列を proj.4 の "plus format" からプロジェクションを構築します。

プロジェクション文字列 `proj_string` は、各プロジェクション仕様の部分が '+' 文字で接頭辞付けされた proj.4 形式で定義されています。例えば：

```
`wgs84 = Projection("+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs")`
```
