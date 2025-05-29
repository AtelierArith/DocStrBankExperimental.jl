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

Plot a comparison of multiple item banks `item_banks`. For an explanation of the options, see: `plot_item_bank`.
