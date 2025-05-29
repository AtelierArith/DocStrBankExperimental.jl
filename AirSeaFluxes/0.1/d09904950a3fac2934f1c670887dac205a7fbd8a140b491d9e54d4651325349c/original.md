```
calc_pco2(T,S,dic,ta,pt=0.0,sit=0.0)
```

Calculate pCO2 for given Temperature(T), Salinity(S), DIC, Alkalinity, etc.. Efficient solver following Follows et al (2005)

```
pco2eq = atmospheric reference pCO2 level (atmospheres)
               for which to find equilibrium dic, csat
      csat = equilibrium total inorganic carbon (mol/m³)
            where 1 T = 1 metric ton = 1000 kg
      ta  = total alkalinity (eq/m³)
      pt  = inorganic phosphate (mol/m³)
      sit = inorganic silicate (mol/m³)
      T   = temperature (degrees C)
      S   = salinity (PSU)
    hg  = first guess of [H+] (10e-8 is a good cold start value)
```
