```
dropdown(options::AbstractDict;
         value = first(values(options)),
         label = nothing,
         multiple = false)
```

オプションのキーがアイテムラベルであるドロップダウンメニュー。`multiple=true` の場合、observable は選択されたすべてのアイテムの値を含む配列を保持します。例: `dropdown(OrderedDict("good"=>1, "better"=>2, "amazing"=>9001))`

`dropdown(values::AbstractArray; kwargs...)`

`dropdown` は `string.(values)` でラベル付けされます。詳細については `dropdown(options::AbstractDict; ...)` を参照してください。
