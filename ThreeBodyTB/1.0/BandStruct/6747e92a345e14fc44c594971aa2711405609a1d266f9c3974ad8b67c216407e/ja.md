```
function plot_bandstr_sym(tbc::tb_crys;  sym_prec = 5e-4, npts=30, efermi = missing, color="blue", MarkerSize=missing, yrange=missing, plot_hk=false, align = "vbm", proj_types = missing, proj_orbs = missing, proj_nums=missing, clear_previous=true, do_display=true, color_spin = ["green", "orange"], spin = :both, nspin = 1, database=missing)
```

バンド構造を、空間群によって決定されたK点のセットを使用してプロットします。このバージョンは、以前のSCF計算からのタイトバインディング結晶オブジェクトを受け取ります。結晶が標準化された単位セルにある場合、SCF計算を繰り返すことはありませんが、そうでない場合は繰り返します。
