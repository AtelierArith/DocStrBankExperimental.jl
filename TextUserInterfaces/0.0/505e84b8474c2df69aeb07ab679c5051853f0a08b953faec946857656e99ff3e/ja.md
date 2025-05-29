```
function ncurses_color([foreground::Symbol, background::Symbol,] attrs::Int = 0; kwargs...)
```

前景色 `foreground`、背景色 `background`、および属性 `attrs` を使用して色フォーマットを適用するためのマスクを返します。

ペア（`foreground`、`background`）が省略された場合、前景色と背景色は変更されません。

# キーワード

  * `bold`: `true` の場合、太字フォーマットマスクを `attrs` に適用します。         (**デフォルト** = `false`)
  * `underline`: `true` の場合、下線フォーマットマスクを `attrs` に適用します。              (**デフォルト** = `false`)
