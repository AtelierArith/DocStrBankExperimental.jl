```
fe_swap = swap_yz_dims(fe_data::FEData)
```

This swaps the `y` and `z` dimensions of the FEData object, which is useful for pTatin as it uses `y` for what is `z` in GMG.
