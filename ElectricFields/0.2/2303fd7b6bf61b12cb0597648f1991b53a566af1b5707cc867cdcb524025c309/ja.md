```
IsotropicMedium(material, d; ω₀)
```

[`IsotropicMedium`](@ref)の便利なコンストラクタです。中心角周波数`ω₀`が提供されると、`material`の分散の線形傾きが`ω₀`で計算されます。この傾きはその後、分散から引かれます。
