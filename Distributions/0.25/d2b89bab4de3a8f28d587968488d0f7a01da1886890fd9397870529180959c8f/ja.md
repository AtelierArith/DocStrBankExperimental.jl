```
Distribution{F<:VariateForm,S<:ValueSupport} <: Sampleable{F,S}
```

`Distribution`は確率分布からランダム値を生成する`Sampleable`です。分布は、`pdf`を使用して実装する確率分布関数（PDF）と、`cdf`を使用して実装する累積分布関数（CDF）を定義します。
