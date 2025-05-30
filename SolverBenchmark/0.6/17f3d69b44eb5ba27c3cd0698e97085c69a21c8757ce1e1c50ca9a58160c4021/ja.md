```
hl = gradient_highlighter(df, col; cmap=:coolwarm)
```

値にカラ―グラデーションを適用するPrettyTablesハイライターで、`cols`で指定された列に適用されます。

### 入力引数

  * `df::DataFrame` ハイライターが適用されるデータフレーム;
  * `col::Symbol` ハイライターが適用される列を示すシンボル。

### キーワード引数

  * `cmap::Symbol` 使用するカラースキーム、ColorSchemesから。
