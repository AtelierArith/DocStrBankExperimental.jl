```
setcolor("gold")
setcolor("darkturquoise")
```

現在の色を名前付きの色に設定します。これは、Colors.jlの定義を使用して文字列をRGBAに変換します。例えば、`setcolor("gold")`や"green"、"darkturquoise"、"lavender"などです。リストは`Colors.color_names`にあります。

現在の不透明度レベルを変更せずに色を変更するには`sethue()`を使用します。

`sethue()`と`setcolor()`は、使用された3つまたは4つの値を返します：

```julia
julia> setcolor(sethue("red")..., .8)
(1.0N0f8, 0.0N0f8, 0.0N0f8, 0.8)

julia> sethue(setcolor("red")[1:3]...)
(1.0N0f8, 0.0N0f8, 0.0N0f8)
```

次のようにすることもできます：

```
using Colors
sethue(colorant"red")
```

[`setcolor`](@ref)も参照してください。
