```
Figure([figsize::Tuple{Float64, Float64}, units::String])
```

指定されたサイズの新しい図を作成します。

図のサイズは、`figsize`（ターゲットの幅と高さを持つ2タプル）と、`units`（単位の略語を持つ文字列："px"はピクセル、"in"はインチ、"cm"はセンチメートル、または"m"はメートル）によって定義されます。引数なしで`Figure()`を使用した場合のデフォルトの寸法は600×450ピクセルです — または、検出されたディスプレイ解像度が高い場合は比例的に増加したサイズになります。このコンストラクタは、"現在の図"を作成されたばかりのものに設定します。
