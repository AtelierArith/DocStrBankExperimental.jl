```
Risk(λ::Real,
     α::Real;
     offset::Union{Dict{Leaf,Float64},Nothing}=nothing,
     bound::Union{Real,Nothing}=nothing,
     penalty::Union{Real,Nothing} = nothing)
```

CVaRリスク測定を、葉ノードでの累積利益に適用することを定義します。

### 必要な引数

`λ`はリスク測定に適用される重みであり（重みの合計は最大で1.0であるべきです）、重みの合計が1.0未満の場合、期待値が残りを補います。

`α`は分布の尾部における確率です。

### オプションの引数

`offset`は各葉ノードに負のオフセットを適用します。これはリスク測定を適用する前に結果の順序を変更するために使用できます。

`bound`を使用すると、これを上限としてCVaR(α)に制約が作成されます。

`penalty`はCVaRに制約が適用される場合、制約を違反することの限界コストが`penalty`になります；`nothing`に設定されている場合、制約違反は許可されません。
