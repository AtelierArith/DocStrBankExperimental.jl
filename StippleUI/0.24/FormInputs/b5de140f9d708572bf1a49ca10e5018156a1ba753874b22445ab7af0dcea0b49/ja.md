```
datefield(args...; kwargs...)
```

テキストフィールドとアイコン、日付ピッカー、ポップアップを組み合わせた複雑な入力タイプです。日付ピッカーはデフォルトで隠されており、アイコンがクリックされると表示されます。ポップアップは、ユーザーが日付ピッカーの外をクリックしたときに日付ピッカーを隠すために使用されます。いくつかの一般的な引数が定義されており、テキストフィールド、アイコン、ポップアップ、日付ピッカーに渡されます。さらに、`textfield_props`、`icon_props`、`popup_proxy_props`、および `datepicker_props` キーワード引数を使用することで、これらのコンポーネントそれぞれに個別にキーワード引数を渡すことができます。

### 例

```julia
datefield("Start date", :start_date, datepicker_props = Dict(:todaybtn => true, :nounset => true), textfield_props = Dict(:bgcolor => "green-1"))
```
