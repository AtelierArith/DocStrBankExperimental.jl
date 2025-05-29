```
dlcap0(electrolyte)
```

Return double layer capacitance at zero voltage for symmetric binary electrolyte. The molarity is defined by the bulk concentration value $c_1^b$.

$$
    c_{dl}=2 \frac{εε_0F^2c_1^b}{RT}
$$

### Example

```jldoctest
using LessUnitful
ely = ElectrolyteData(c_bulk=fill(0.01ufac"mol/dm^3",2))
round(dlcap0(ely),sigdigits=5) |> u"μF/cm^2"
# output

22.847 μF cm^-2
```
