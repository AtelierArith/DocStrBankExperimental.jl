```
picard_group(O::AlgAssAbsOrd, prepare_ref_disc_log::Bool = false)
  -> FinGenAbGroup, MapPicardGroup
```

与えられた順序 $O$ は $\mathbb Q$ 上の可換代数におけるものであり、この関数は $O$ のピカール群を返します。`prepare_ref_disc_log` が `true` の場合、非最大順序における洗練された離散対数の計算のための（おそらく高価な）準備が行われます。
