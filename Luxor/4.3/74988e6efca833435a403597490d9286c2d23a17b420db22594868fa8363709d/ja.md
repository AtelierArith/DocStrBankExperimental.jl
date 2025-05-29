```
textbox(lines::Array, pos::Point=O;
    leading = 12,
    linefunc::Function = (linenumber, linetext, startpos, height) -> (),
    alignment=:left)
```

配列 `lines` の文字列を垂直に下向きに描画します。`leading` は各行の間隔を制御し（デフォルトは 12）、`alignment` は水平方向の配置を決定します（デフォルトは `:left`）。

オプションとして、各行の前に関数 `linefunc(linenumber, linetext, startpos, height)` を実行します。

次の行が描画される位置を返します。

また、指定された幅に行が収まるようにテキストを修正する `textwrap()` も参照してください。
