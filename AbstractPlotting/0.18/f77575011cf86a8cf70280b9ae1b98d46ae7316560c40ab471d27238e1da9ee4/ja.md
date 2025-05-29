```
title(
    [scene=current_scene(), ], string;
    align = (:center, :bottom), textsize = 30, parent = Scene(), formatter = string, kw...
)
```

シーンに内容 `string` のタイトルを追加します。`string` に渡される値が実際には文字列でない場合は、`formatter` kwarg に `Function` を渡してください。
