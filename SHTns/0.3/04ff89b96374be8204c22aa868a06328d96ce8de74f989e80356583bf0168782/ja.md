```
analys!(cfg::SHTnsCfg, v, qlm)
analys!(cfg::SHTnsCfg, utheta, uphi, slm, tlm)
analys!(cfg::SHTnsCfg, ur, utheta, uphi, qlm, slm, tlm)
```

スカラー、2Dまたは3Dフィールドの空間データを球面調和係数にインプレースで変換します。

!!! warning
    この関数は入力配列 `v`、`ur`、`utheta` および `uphi` を変更します。

