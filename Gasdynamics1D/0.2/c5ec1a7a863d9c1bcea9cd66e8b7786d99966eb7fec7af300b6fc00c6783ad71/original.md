```
Entropy(s1::Entropy,M1::MachNumber,NormalShock[;gas=Air])
```

Return the entropy after a normal shock, given the entropy before the shock `s1` and the Mach number before the shock `M1`, using the equation

$s_2 - s_1 = c_v \ln \left(1 + \dfrac{2\gamma}{\gamma+1}(M_1^2-1)\right) - c_p \ln \left( \dfrac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}\right)$
