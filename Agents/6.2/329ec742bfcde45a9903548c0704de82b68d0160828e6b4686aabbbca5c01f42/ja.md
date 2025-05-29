```
add_interaction!(ax)
add_interaction!(ax, p::_ABMPlot)
```

モデル制御ボタンとパラメータスライダーを、プロットキーワード `add_controls`（trueの場合）および `params`（空でない場合）に従って追加します。ボタンとスライダーは、`ax`の位置の下にある新しいレイアウト位置に隣接して配置されます。
