```
ascii_show(stream, img, colordepth::TermColorDepth, encoder::Symbol=:auto, maxsize::Tuple=displaysize(io))
```

与えられた画像 `img` をユニコード文字と端末の色を使用して表示します。`img` は `Colorant` の配列でなければなりません。

  * `maxsize` は、結果の画像に使用される文字列の最大数（行、列）を指定します。大きな画像は自動的に `restrict` を使用して縮小されます。

REPL で作業している場合、関数は現在の表示サイズに基づいてエンコーディングを選択しようとします。画像は表示に収まるようにダウンサンプリングされます（`restrict` を使用）。
