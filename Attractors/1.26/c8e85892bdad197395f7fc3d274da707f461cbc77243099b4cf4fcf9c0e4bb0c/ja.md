```
plot_basins_attractors_curves(
    fractions_cont, attractors_cont, a2rs [, prange]
    kwargs...
)
```

[`plot_basins_curves`](@ref) と [`plot_attractors_curves`](@ref) の便利な組み合わせで、凡例、色、マーカーなどを共有するマルチパネルプロットです。この関数では、`a2rs` を実数にマッピングする関数の `Vector` として指定できます。基盤の分数プロットの下に、`a2rs` の各エントリに対して追加のパネルが作成されます。`a2rs` は単一の関数でも構いません。その場合は、1つのパネルのみが作成されます。
