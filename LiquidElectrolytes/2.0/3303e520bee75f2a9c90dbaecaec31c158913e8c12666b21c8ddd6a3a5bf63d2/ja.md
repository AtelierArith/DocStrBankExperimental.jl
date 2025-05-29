```
debyelength(electrolyte)
```

対称二元電解質のデバイ長を返します。モラリティはバルク濃度値 $c_1^b$ によって定義されます。

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
