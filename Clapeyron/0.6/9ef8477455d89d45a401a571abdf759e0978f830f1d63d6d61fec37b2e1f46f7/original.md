```
equivol_cross_second_virial(model::EoSModel,T,p_exp = 200000.0)
```

calculates the second cross virial coefficient, by simulating the mixing of equal volumes of pure gas, at T,P conditions. The equal volume of each pure gas sets an specific molar amount for each component. Details of the experiment can be found at [1].

## Example

```
model = SAFTVRQMie(["helium","neon"])
B12 = equivol_cross_second_virial(model,)

```

## References

1. Brewer, J., & Vaughn, G. W. (1969). Measurement and correlation of some interaction second virial coefficients from − 125° to 50°C. I. The Journal of Chemical Physics, 50(7), 2960–2968. [doi:10.1063/1.1671491](https://doi.org/10.1063/1.1671491)
