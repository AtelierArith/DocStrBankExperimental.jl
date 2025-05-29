```
P0OverP0Star(M::MachNumber,RayleighFlow[;gas=Air]) -> PressureRatio
```

Compute the ratio of stagnation pressure to sonic stagnation pressure for the given Mach number for Rayleigh flow, using the equation

$\dfrac{p_0}{p_0^*} = \dfrac{(\gamma+1)}{1+\gamma M^2} \left[ \left( \dfrac{1}{\gamma+1} \right)\left(2 + (\gamma-1) M^2\right)\right]^{\gamma/(\gamma-1)}$
