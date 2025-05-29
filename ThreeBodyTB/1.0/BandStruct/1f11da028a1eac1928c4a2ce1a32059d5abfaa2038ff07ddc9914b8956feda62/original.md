```
function plot_compare_dft(tbc, bs; tbc2=missing)
```

Plots a band structure comparison between a tight-binding crystal object (`tb_crys`) and a band structure directly from dft (either a `dftout` or `bs` object). 

The k-points are fixed by the `bs` object.

`tbc2` is an optional second `tbc_crys`.
