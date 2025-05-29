```
function makedftout(crys::crystal, energy::Number, energy_smear::Number,  forces, stress, bandstruct=missing; prefix="PREFIX", outdir="TMPDIR", tot_charge=0.0)
```

Constructor for dftout. Usually called by function that loads DFT output files, not called directly.
