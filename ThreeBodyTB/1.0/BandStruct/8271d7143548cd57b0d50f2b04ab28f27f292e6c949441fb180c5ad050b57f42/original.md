```
function plot_bandstr_sym(c::crystal; sym_prec = 5e-4, npts=30, efermi = missing, color="blue", MarkerSize=missing, yrange=missing, plot_hk=false, align = "vbm", proj_types = missing, proj_orbs = missing, proj_nums=missing, clear_previous=true, do_display=true, color_spin = ["green", "orange"], spin = :both, nspin = 1, database=missing)
```

Plots the band structure using a set of K-points determined by the space group. Will standardize the crystal structure and run the SCF  calculation automatically. Conventions similar to Setyawan and Curtarolo CMS 2010 as well as the jarvis-tools package. Other options similar to `plot_bandstr`
