```
readvcells(meta::MetaVLSV, cid::Int; species="proton") -> vcellids, vcellf
```

`meta`に関連付けられたID `cid`の空間セルから`species`の速度セルを読み取り、速度セルIDのマップ`vcellids`と対応する値`vcellf`を返します。
