```
SyntheticRule{probability::Float64[, item::Union{Nothing, Integer}, match::Function])
```

累積「クリック率」のためのマッチングルール。アイテムインデックスが与えられたとき、`match` が `true` を返すとサンプリング時の受け入れ確率が増加します。`match` は特徴名 => 値の辞書を受け取ります。

```julia
rules = SyntheticRule[]

push!(rules, SyntheticRule(0.001))
push!(rules, SyntheticRule(0.01, 3))
push!(rules, SyntheticRule(0.30, 1, s -> s["Age"] >= 1980 && s["Age"] <= 1989 && s["Geo"] == "New York"))
push!(rules, SyntheticRule(0.30, 2, s -> s["Age"] >= 1950 && s["Age"] <= 1959 && s["Geo"] == "New York"))
push!(rules, SyntheticRule(0.30, 2, s -> s["Age"] >= 1980 && s["Age"] <= 1989 && s["Geo"] == "Arizona"))
push!(rules, SyntheticRule(0.30, 1, s -> s["Age"] >= 1950 && s["Age"] <= 1959 && s["Geo"] == "Arizona"))
```
