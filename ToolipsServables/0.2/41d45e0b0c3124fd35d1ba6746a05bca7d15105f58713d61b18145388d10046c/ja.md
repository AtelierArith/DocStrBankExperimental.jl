```julia
keyframes(name::String) -> ::KeyFrames
```

`:keyframes` `Animation`を構築します。これは、`keyframes!`を使用してフレームを追加できます。`keyframes!`には、アニメーションを作成するために、`to`、`from`、またはスタイルペアを持つパーセンテージを提供します。

```example
frames = keyframes("fadein")

keyframes!(frames, from, "opacity" => 0percent)
keyframes!(frames, to, "opacity" => 100percent)
# これで、`style!`を使用できるようになり、`Animation`を`StyleComponent`として`write!`することを確認します。
mycomp = h2("heading", text = "このテキストはフェードインします")

style!(mycomp, frames)
```
