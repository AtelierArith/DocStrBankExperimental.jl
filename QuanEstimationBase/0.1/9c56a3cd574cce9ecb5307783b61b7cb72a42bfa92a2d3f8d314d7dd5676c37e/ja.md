```
CFIM_obj(;M=nothing, W=nothing, eps=GLOBAL_EPS)
```

目的関数としてCFI [$\mathrm{Tr}(WI^{-1})$] を選択します。ここで、$W$ は重み行列、$I$ はCFIMです。

  * `M`: 正の演算子値測度（POVM）の集合。デフォルトの測定は、ランク1の対称情報完全POVM（SIC-POVM）の集合です。
  * `W`: 重み行列。
  * `eps`: マシンエプシロン。
