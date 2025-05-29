```
function create_window(nlines::Integer, ncols::Integer, begin_y::Integer, begin_x::Integer, id::String = ""; bcols::Integer = 0, blines::Integer = 0, border::Bool = true, border_color::Int = -1, title::String = "", title_color::Int = -1)
```

ウィンドウを作成します。新しいウィンドウのサイズは `nlines × ncols` で、原点はルートウィンドウの `(begin_y, begin_x)` 座標に配置されます。ウィンドウID `id` は、グローバルウィンドウリスト内で新しいウィンドウを識別するために使用されます。

# キーワード

  * `bcols`: ウィンドウバッファ内の列数。この値は、ウィンドウの表示可能部分 (`ncols`) に少なくとも収まるように自動的に増加します。 (**デフォルト** = 0)
  * `blines`: ウィンドウバッファ内の行数。この値は、ウィンドウの表示可能部分 (`nlines`) に少なくとも収まるように自動的に増加します。 (**デフォルト** = 0)
  * `border`: `true` の場合、ウィンドウには境界線が表示されます。 (**デフォルト** = `true`)
  * `border_color`: 境界線を印刷するために使用されるカラーマスク。関数 `ncurses_color` を参照してください。負の値の場合、色は変更されません。 (**デフォルト** = -1)
  * `focusable`: `true` の場合、ウィンドウはフォーカスを持つことができます。そうでない場合、すべてのフォーカス要求は拒否されます。 (**デフォルト** = `true`)
  * `title`: ウィンドウのタイトルで、`border` が `true` の場合のみ印刷されます。 (**デフォルト** = "")
  * `title_color`: タイトルを印刷するために使用されるカラーマスク。関数 `ncurses_color` を参照してください。負の値の場合、色は変更されません。 (**デフォルト** = -1)
