```
function set_window_title(win::Window, title::AbstractString; ...)
```

ウィンドウ `win` のタイトルを `title` に設定します。

# キーワード

  * `title_color`: タイトルを表示するために使用される色マスク。関数 `ncurses_color` を参照してください。負の値の場合、色は変更されません。(**デフォルト** = -1)
