```
FlashSpecifications(;v,T,p,h,s,u,q)
```

Struct that holds two specifications for a general flash. The keyword arguments have the following meaning:

  * `T`: temperature
  * `v`: total volume
  * `p`: pressure
  * `h`: enthalpy
  * `s`: entropy
  * `u`: internal energy
  * `q`: vapour fraction

## Examples:

```
specs = FlashSpecifications(p = 101325,T = 298.15) #PT flash
specs = FlashSpecifications(Clapeyron.pressure,101325,Clapeyron.temperature,298.15) #equivalent
```
