```julia
plot_item_bank(
    item_bank::FittedItemBanks.AbstractItemBank;
    fig,
    items,
    labeller,
    zero_symmetric,
    include_outcome_toggles,
    item_selection,
    include_legend
) -> Makie.Figure

```

アイテムバンク `item_bank` をアイテム `items` とともにプロットし、ラベラー `labeller` を使用してアイテムにラベルを付けます。

各アイテムと各結果のために線が描画されます。アイテムバンクのドメインが x 軸の制限を決定するために使用されます。`zero_symmetric` を使用すると、ドメインをゼロを中心に対称に強制することができます。

`include_outcome_toggles` が true の場合、結果を表示/非表示にするためのトグルグリッドが描画されます。`item_selection` が :toggles の場合、アイテムを表示/非表示にするためのトグルグリッドが描画され、:menu の場合は、単一のアイテムを選択できるメニューが使用されます。
