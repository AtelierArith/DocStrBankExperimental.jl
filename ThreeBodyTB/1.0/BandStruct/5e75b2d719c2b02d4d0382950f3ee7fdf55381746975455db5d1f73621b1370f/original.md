```
function plot_bandstr_dos(tbc::tb_crys)
```

Plot symmetry-derived k-lines and DOS layout out together. This version takes in `tb_crys` object from a previous SCF calculation. Will need re-run SCF if `tbc.crys` is not standardized.

See `plot_bandstr_sym` and `dos`
