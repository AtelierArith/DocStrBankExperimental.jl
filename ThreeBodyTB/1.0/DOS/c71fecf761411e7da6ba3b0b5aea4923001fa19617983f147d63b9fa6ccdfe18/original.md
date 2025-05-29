```
function dos(tbc::tb_crys; grid=missing, smearing=0.04, npts=missing, proj_type=missing, do_display=true)
```

DOS, mostly for testing.

  * `npts` is number of energies
  * `proj_type` can be `"none"`, `"atomic"`, or `"orbital"`
  * `do_display=false` will suppress the actual plot

The combination of `smearing` and `grid` are important to get converged results.

See also `dos`

`return energies, dos, projected_dos, pdos_names`
