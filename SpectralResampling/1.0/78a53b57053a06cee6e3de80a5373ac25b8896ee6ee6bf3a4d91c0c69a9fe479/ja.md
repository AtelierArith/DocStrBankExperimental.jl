```
get_logarithmic_λ(λ[, log_spacing])
```

線形に間隔を空けた波長グリッド `λ` に基づいて、対数的に間隔を空けた波長グリッドを計算します。要素間の間隔（対数空間で）をオプションで指定することができます `log_spacing`。例えば、`lnλ` が対数的に間隔を空けた波長グリッドである場合、`log_spacing` は `log_spacing = log(lnλ[2]/lnλ[1]) = log(lnλ[end]/lnλ[end-1])` と定義されます。
