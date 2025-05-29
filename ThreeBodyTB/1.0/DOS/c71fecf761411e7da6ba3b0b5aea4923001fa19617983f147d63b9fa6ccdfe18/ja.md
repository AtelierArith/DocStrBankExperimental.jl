```
function dos(tbc::tb_crys; grid=missing, smearing=0.04, npts=missing, proj_type=missing, do_display=true)
```

DOS、主にテスト用。

  * `npts` はエネルギーの数
  * `proj_type` は `"none"`、`"atomic"`、または `"orbital"` であることができます
  * `do_display=false` は実際のプロットを抑制します

`smearing` と `grid` の組み合わせは、収束した結果を得るために重要です。

`dos` も参照してください。

`return energies, dos, projected_dos, pdos_names`
