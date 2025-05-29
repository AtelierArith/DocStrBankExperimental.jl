```
polytext!(c::AbstractCoordinateSystem, str::String, sty::PolyText.Style;
    scripting=false, linelimit=typemax(Int), verbose=false)
```

文字列 `str` を指定されたスタイルでセルまたは座標系 `c` にレンダリングします。

# キーワード引数

  * `scripting`: 上付き文字および下付き文字のために特殊文字 `^`, `_`, `{`, および `}` を割り当てるためのブールパラメータ。LaTeXと同じ使用法に従います。
  * `linelimit`: 1行あたりの最大文字数を設定し、`str` が `linelimit` より長い場合は新しい行に続けます。
  * `verbose`: 文字辞書に関する情報を出力します。
