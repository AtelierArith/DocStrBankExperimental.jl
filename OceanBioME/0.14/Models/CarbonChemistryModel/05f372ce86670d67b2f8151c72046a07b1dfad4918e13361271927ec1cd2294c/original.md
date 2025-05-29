```
(p::CarbonChemistry)(; DIC, T, S, Alk = 0, pH = nothing,
                       return_pH = false,
                       boron = 0.000232 / 10.811 * S / 1.80655,
                       sulfate = 0.14 / 96.06 * S / 1.80655,
                       fluoride = 0.000067 / 18.9984 * S / 1.80655,
                       silicate = 0,
                       phosphate = 0,
                       upper_pH_bound = 14,
                       lower_pH_bound = 0)
```

Calculates `fCO₂` in sea water with `DIC`, `Alk`alinity, `T`emperature, and `S`alinity unless `pH` is specified, in which case intermediate computation of `pH` is skipped and `pCO₂` is calculated from the `DIC`, `T`, `S` and `pH`.

Alternativly, `pH` is returned if `return_pH` is `true`.
