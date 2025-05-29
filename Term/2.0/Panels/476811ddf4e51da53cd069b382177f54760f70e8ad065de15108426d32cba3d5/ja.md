```
macro nested_panels(layout_call)
```

複数のネストされた `Panel` のレイアウトを自動化するためのマクロです。パネルの幅は、各ネストレベルの深さに基づいて自動的に調整されます。

`fix_layout_width` を再帰的に使用して、各 `Panel` にキーワード引数 `width` を追加します。
