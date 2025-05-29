`@manipulate expr`

`@manipulate`マクロを使用すると、ウィジェットを使って任意の式を操作できます。`expr`は`for`ループである必要があります。`for`ループの変数は、[`widget`](@ref)関数を使用してウィジェットに変換されます（範囲は`slider`に、オプションのリストは`togglebuttons`に変わりますなど）。`for`ループの本体はウィジェットの下に表示され、ウィジェットの値が変更されると自動的に更新されます。

`throttle = df`を使用すると、出力は小さな時間間隔`dt`の後にのみ更新されます（更新がコストのかかる場合に便利で、たとえばスライダーを動かすときに複数の更新を防ぎます）。

## 例

```julia
using Colors

@manipulate for r = 0:.05:1, g = 0:.05:1, b = 0:.05:1
    HTML(string("<div style='color:#", hex(RGB(r,g,b)), "'>Color me</div>"))
end

@manipulate throttle = 0.1 for r = 0:.05:1, g = 0:.05:1, b = 0:.05:1
    HTML(string("<div style='color:#", hex(RGB(r,g,b)), "'>Color me</div>"))
end
```

[`@layout!`](@ref)を使用して、操作ブロックのレイアウトを調整できます：

```julia
using Interact

ui = @manipulate throttle = 0.1 for r = 0:.05:1, g = 0:.05:1, b = 0:.05:1
    HTML(string("<div style='color:#", hex(RGB(r,g,b)), "'>Color me</div>"))
end
@layout! ui dom"div"(observe(_), vskip(2em), :r, :g, :b)
ui
```
