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

Plot an item bank `item_bank` with items `items` using the labeller `labeller` to label the items.

Lines are drawn for each item and each outcome. The domain of the item bank is used to determine the x-axis limits. You can use `zero_symmetric` to force the domain to be symmetric about zero.

If `include_outcome_toggles` is true, then a toggle grid is drawn to show/hide the outcomes. If `item_selection` is :toggles, then a toggle grid is drawn to show/hide the items, for :menu a menu is used allowing a single item to be choseshowenn.
