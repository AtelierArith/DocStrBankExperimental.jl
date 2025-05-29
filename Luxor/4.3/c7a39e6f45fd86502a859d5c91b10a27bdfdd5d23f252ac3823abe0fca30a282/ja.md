```
textoutlines(s::String, pos::Point=O;
    action=:none,
    halign=:left,
    valign=:baseline,
    startnewpath=true)
```

テキストをポリゴンに変換し、`action`を適用します。(ToyAPI)

デフォルトでは、この関数は現在のパスを破棄しますが、`startnewpath=false`を使用すると破棄されません。

`textpath()`も参照してください。`textpath()`はベジェ曲線を保持しますが、`textoutlines()`はフラットな曲線を返します。

TODO ブール値よりも有用なものを返す。
