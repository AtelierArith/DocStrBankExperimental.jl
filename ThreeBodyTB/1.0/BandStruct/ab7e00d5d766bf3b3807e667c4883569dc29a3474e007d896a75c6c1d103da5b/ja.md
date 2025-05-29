```
function plot_bandstr_dos(c::crystal; sym_prec = 5e-4, npts=30, efermi = missing,color="blue", MarkerSize=missing,yrange=missing,plot_hk=false, align = "fermi",  proj_types = missing, proj_orbs = missing, proj_nums=missing, clear_previous=true, do_display=true, color_spin = ["green", "orange"],  spin = :both, nspin = 1, database=missing, smearing = 0.025)
```

標準化された結晶構造でSCFを実行し、対称性に基づいて導出されたkラインに沿ったバンド構造とDOSを計算します。それらを横に並べてプロットします。

`plot_bandstr_sym`および`dos`を参照してください。
