```julia
plot_item_bank_comparison(
    item_banks::AbstractVector;
    items,
    labeller,
    include_outcome_toggles,
    include_item_toggles,
    ignore_domain_indices
) -> Makie.Figure

```

複数のアイテムバンク `item_banks` の比較をプロットします。オプションの説明については、`plot_item_bank` を参照してください。
