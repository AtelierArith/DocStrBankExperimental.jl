```
function plot_bandstr_dos(c::crystal; sym_prec = 5e-4, npts=30, efermi = missing,color="blue", MarkerSize=missing,yrange=missing,plot_hk=false, align = "fermi",  proj_types = missing, proj_orbs = missing, proj_nums=missing, clear_previous=true, do_display=true, color_spin = ["green", "orange"],  spin = :both, nspin = 1, database=missing, smearing = 0.025)
```

Run SCF in standardized crystal structure and calculate band structure along symmetry-derived k-lines, as well as the DOS. Then plot them layed out side-by-side.

See `plot_bandstr_sym` and `dos`
