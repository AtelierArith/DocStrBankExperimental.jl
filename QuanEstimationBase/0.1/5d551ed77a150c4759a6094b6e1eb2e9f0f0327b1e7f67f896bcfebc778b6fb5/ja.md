```
QFIM_obj(;W=nothing, eps=GLOBAL_EPS, LDtype::Symbol=:SLD)
```

目的関数としてQFI [$\mathrm{Tr}(WF^{-1})$] を選択し、$W$は重み行列、$F$はQFIMです。

  * `W`: 重み行列。
  * `eps`: マシンイプシロン。
  * `LDtype`: 目的関数として設定できるQFI（QFIM）のタイプ。オプションは`:SLD`（デフォルト）、`:RLD`、および`:LLD`です。
