```
Save( fn, mt, sol :: GrumpsSolution; keywords... )
```

`sol`に保存された解を、mimeタイプ`mt`を持つファイル名`fn`に保存します。

以下に説明されているいくつかのキーワードがあり、いくつかは特定のmimeタイプでは無視されます。許可されているmimeタイプは`text/plain`、`text/csv`、および`text/tex`です。

| キーワード              | 説明         | デフォルト   |
|:------------------ |:---------- |:------- |
| `colsep`           | 列の区切り      | `","`   |
| `adorned`          | 出力を美しくする？  | `true`  |
| `printθ`           | θの結果を印刷する？ | `true`  |
| `printβ`           | βの結果を印刷する？ | `true`  |
| `printδ`           | δの結果を印刷する？ | `false` |
| `printconvergence` | 収束統計を表示する？ | `true`  |
