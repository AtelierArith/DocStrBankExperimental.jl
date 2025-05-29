```
mz(charged_chemical::AbstractChemical)
mz(chemical::AbstractChemical, adduct::AbstractAdduct)
mz(chemical::AbstractChemical, adduct::AbstractString)
mz(adduct_ion::AbstractAdductIon, adduct = ionadduct(adduct_ion))
mz(isobars::Isobars) 
mz(isobars::Isobars, adduct)
```

`charged_chemical`、`adduct_ion`、`isobars`、または`adduct`を持つ`chemical`のm/zを計算します。これは`mw(cc) / ncharge(cc)`に相当します。
