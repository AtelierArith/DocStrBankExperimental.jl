`onchange(w::AbstractWidget, change = w[:changes])`

`w`と同一のウィジェットを返しますが、`change`のみに基づいて更新されます。スライダーの場合はリリース時に対応し、テキストボックスの場合はフォーカスを失ったときに対応します。

## 例

```julia
sld = slider(1:100) |> onchange # リリース時に更新
txt = textbox("ここに書いてください") |> onchange # フォーカスを失ったときに更新
```
