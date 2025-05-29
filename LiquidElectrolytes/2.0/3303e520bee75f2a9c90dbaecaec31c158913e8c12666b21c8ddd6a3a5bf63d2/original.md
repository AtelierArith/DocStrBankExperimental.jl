```
debyelength(electrolyte)
```

Return debye length for symmetric binary electrolyte. The molarity is defined by the bulk concentration value $c_1^b$.

$$
    l_{debye}=\sqrt{RT\frac{εε_0}{F^2c_1^b}}
$$

```jldoctest
using LessUnitful
ely = ElectrolyteData(c_bulk=fill(0.01ufac"mol/dm^3",2))
round(debyelength(ely),sigdigits=5) |> u"nm"
# output

4.3018 nm
```
