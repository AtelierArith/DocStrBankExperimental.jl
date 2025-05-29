```
texttrack(txt, pos, tracking;
    action=:fill,
    halign=:left,
    valign=:baseline,
    startnewpath=true)
texttrack(txt, pos, tracking, fontsize;
    action=:fill,
    halign=:left,
    valign=:baseline,
    startnewpath=true)
```

`txt`のテキストを`pos`に左揃えで配置し、`tracking`の値を使用してテキストの文字間隔（'track'）を調整します。

トラッキングの単位は現在のフォントサイズに依存します。12ポイントのフォントでは、1emは12ポイントに相当します。1ポイントは約0.35mm、1emは約4.2mm、トラッキングの1000単位は約4.2mmです。したがって、12ポイントフォントのトラッキング値が1000の場合、各文字の間に約4mmのスペースが配置されます。

負の値は文字間隔を明らかに狭くします。

各文字に適用されるテキスト描画アクションはデフォルトで`textoutlines(... :fill)`です。

`startnewpath`がtrueの場合、各文字は個別に処理されます。テキストをクリップしてトラッキングするには、クリップアクションを指定し、各文字のためにクリッピングパスをリセットしないようにします。

```julia
newpath()
texttrack(t, O + (0, 80), 200, action=:clip, startnewpath=false)
...
clipreset()
```

TODO 組み合わせ文字（例："̈"）を持つ文字列を修正することは可能ですか？
