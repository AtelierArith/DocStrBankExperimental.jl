```
function plot_bandstr_sym(tbc::tb_crys;  sym_prec = 5e-4, npts=30, efermi = missing, color="blue", MarkerSize=missing, yrange=missing, plot_hk=false, align = "vbm", proj_types = missing, proj_orbs = missing, proj_nums=missing, clear_previous=true, do_display=true, color_spin = ["green", "orange"], spin = :both, nspin = 1, database=missing)
```

Plots the band structure using a set of K-points determined by the space group. This version takes in a tight-binding crystal object from a pervious SCF calculation.  If the crystal is in the standardized unit cell, then it will not repeat the SCF calculation, but otherwise it will.
