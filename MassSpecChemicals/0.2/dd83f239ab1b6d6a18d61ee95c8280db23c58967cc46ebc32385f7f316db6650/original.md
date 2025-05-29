```
mz(charged_chemical::AbstractChemical)
mz(chemical::AbstractChemical, adduct::AbstractAdduct)
mz(chemical::AbstractChemical, adduct::AbstractString)
mz(adduct_ion::AbstractAdductIon, adduct = ionadduct(adduct_ion))
mz(isobars::Isobars) 
mz(isobars::Isobars, adduct)
```

Calculate m/z of `charged_chemical`, `adduct_ion` `isobars` or `chemical` with adduct `adduct`. It is equivalent to `mw(cc) / ncharge(cc)`.
