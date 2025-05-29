```
dlcap0(electrolyte)
```

対称二元電解質のゼロ電圧における二重層キャパシタンスを返します。モラリティはバルク濃度値 $c_1^b$ によって定義されます。

$$
    c_{dl}=2 \frac{εε_0F^2c_1^b}{RT}
$$

### 例

```jldoctest
using LessUnitful
ely = ElectrolyteData(c_bulk=fill(0.01ufac"mol/dm^3",2))
round(dlcap0(ely),sigdigits=5) |> u"μF/cm^2"
# 出力

22.847 μF cm^-2
```
