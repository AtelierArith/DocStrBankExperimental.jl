```
photosynthesis(par::C3, PAR = 1000.0, RH = 0.75, Tleaf = 298.0, Ca = 400.0, O2 = 210e3, gb = 0.5, net = true)
photosynthesis(par::C4, PAR = 1000.0, RH = 0.75, Tleaf = 298.0, Ca = 400.0, O2 = 210e3, gb = 0.5, net = true)
photosynthesis(par::C3Q, PAR = 1000.0μmol/m^2/s, RH = 0.75, Tleaf = 298.0K, Ca = 400.0μmol/mol, O2 = 210e3μmol/mol, gb = 0.5mol/m^2/s, net = true)
photosynthesis(par::C4Q, PAR = 1000.0μmol/m^2/s, RH = 0.75, Tleaf = 298.0K, Ca = 400.0μmol/mol, O2 = 210e3μmol/mol, gb = 0.5mol/m^2/s, net = true)
```

Calculate net or gross CO2 assimilation (umol/m2/s) and stomatal condutance to fluxes of CO2 (mol/m2/s) as a function of  photosynthetically active radiation (PAR, umol/m2/s), relative humidity (RH), leaf temperature (Tleaf, K), air CO2 partial pressure (Ca, μmol/mol), oxygen (O2, μmol/mol) and boundary layer  conductance to CO2 (gb, mol/m2/s). Environmental inputs must be scalar. The argument `net` indicates whether the net or gross CO2 assimilation should be returned.
