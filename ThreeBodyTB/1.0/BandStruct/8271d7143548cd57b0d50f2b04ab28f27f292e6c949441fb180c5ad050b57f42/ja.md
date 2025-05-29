```
function plot_bandstr_sym(c::crystal; sym_prec = 5e-4, npts=30, efermi = missing, color="blue", MarkerSize=missing, yrange=missing, plot_hk=false, align = "vbm", proj_types = missing, proj_orbs = missing, proj_nums=missing, clear_previous=true, do_display=true, color_spin = ["green", "orange"], spin = :both, nspin = 1, database=missing)
```

バンド構造を、空間群によって決定されたK点のセットを使用してプロットします。結晶構造を標準化し、SCF計算を自動的に実行します。SetyawanとCurtarolo CMS 2010およびjarvis-toolsパッケージに似た慣習。その他のオプションは`plot_bandstr`に似ています。
