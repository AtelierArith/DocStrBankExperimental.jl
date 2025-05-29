```
function Float64_threshold()
function Float64_threshold(threshold::Float)
```

浮動小数点計算のための閾値を返します。ほとんどの場所で、この値未満の任意の数はゼロとして扱われます。例えば、`cutoff`で。デフォルト: `1e-15`。

オプションで、入力`threshold`に応じて閾値を変更します。
