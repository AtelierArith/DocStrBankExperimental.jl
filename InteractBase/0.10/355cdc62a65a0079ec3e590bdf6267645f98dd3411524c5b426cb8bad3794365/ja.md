```
function rangeslider(vals::AbstractArray;
                value=medianelement(vals),
                label=nothing, readout=true,
                orientation="horizontal",
                direction="ltr", kwargs...)
```

`vals`の値を取るスライダーウィジェットを作成し、いくつかの「ハンドル」を受け入れます。範囲を選択したい場合は、`value`に2つの値を持つベクトルを渡します。垂直スライダーを作成するには、`orientation="vertical"`キーワード引数を使用します。デフォルトでは、スライダーは上から下、左から右ですが、`direction="rtl"`キーワード引数を使用して変更できます。
