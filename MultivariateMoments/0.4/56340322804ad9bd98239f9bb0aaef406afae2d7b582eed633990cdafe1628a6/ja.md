```
struct AtomicMeasure{T, AT, V} <: AbstractMeasureLike{T}
    variables::V                           # 変数のベクトル/タプル
    atoms::Vector{WeightedDiracMeasure{T, AT}} # 測度の原子
end
```

測度が*原子的*であると言われるのは、それが重み付きディラック測度の和である場合です。例えば、$\eta = 2 \delta_{(1, 0)} + 3 \delta_{(1/2, 1/2)}$は原子的測度であり、これはそれぞれ2と3で重み付けされた$(1, 0)$と$(1/2, 1/2)$に中心を持つディラックの和だからです。つまり、$\mathbb{E}_{\eta}[p] = 2p(1, 0) + 3p(1/2, 1/2)$です。

`AtomicMeasure`構造体は原子的測度を格納し、`variables`には変数が含まれ、`atoms`には測度の原子が含まれます。
