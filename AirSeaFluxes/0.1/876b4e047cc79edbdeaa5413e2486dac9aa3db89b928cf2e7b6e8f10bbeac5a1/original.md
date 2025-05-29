```
bulkformulae(atemp,aqh,speed,sst,hu=10,ht=2,hq=2,zref=10,atmrho=1.2)
```

Units: atemp  - mean air temperature (K)  at height ht (m) aqh    - mean air humidity (kg/kg) at height hq (m) speed  - mean wind speed (m/s)     at height hu (m) sst    - sea surface temperature (K)

Bulk formulae formulation:

```
wind stress = (ust,vst) = rhoA * Cd * Ws * (del.u,del.v)
Sensib Heat flux = fsha = rhoA * Ch * Ws * del.T * CpAir
Latent Heat flux = flha = rhoA * Ce * Ws * del.Q * Lvap
                 = -Evap * Lvap
```

with Cd,Ch,Ce = drag coefficient, Stanton number and Dalton number respectively [no-units], function of height & stability, and

```
Ws = wind speed = sqrt(del.u^2 +del.v^2)
del.T = Tair - Tsurf
del.Q = Qair - Qsurf
```
