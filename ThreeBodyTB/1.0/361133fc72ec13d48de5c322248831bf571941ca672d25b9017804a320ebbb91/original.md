```
scf_energy_force_stress(tbc::tb_crys; database = missing, smearing = 0.01, grid = missing)
```

Calculate energy, force, and stress for a tight binding crystal object. This allows the calculation to run without re-doing the SCF calculation. Assumes SCF already done!

returns energy, force, stress, tight*binding*crystal_object
