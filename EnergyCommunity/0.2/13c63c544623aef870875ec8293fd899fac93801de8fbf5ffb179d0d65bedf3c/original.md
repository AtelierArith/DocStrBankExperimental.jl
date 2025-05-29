```
plot_sankey(ECModel::AbstractEC, sank_data::Dict)
```

Function to plot the Sankey diagram representing the energy flows across the energy community. This function can be used to plot the sankey diagram of already processed data sank_data.

## Inputs

ECModel : AbstractEC     Energy Community model name_units : (optional) Vector     Labels used for the sankey diagram with the following order:     "Market buy", [users labels], "Community", "Market sell", [users labels]
