`widget(args...; kwargs...)`

自動的にJuliaの型を適切なウィジェットに変換します。`kwargs`は、より特定のウィジェット関数に渡されます。

## 例

```julia
map(display, [
    widget(1:10),                 # スライダー
    widget(false),                # チェックボックス
    widget("text"),               # テキストボックス
    widget(1.1),                  # スピンボックス
    widget([:on, :off]),          # トグルボタン
    widget(Dict("π" => float(π), "τ" => 2π)),
    widget(colorant"red"),        # カラーピッカー
    widget(Dates.today()),        # 日付ピッカー
    widget(Dates.Time()),         # 時間ピッカー
    ]);
```
