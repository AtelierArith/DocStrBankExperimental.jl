```
rolllist(d :: Dice; generator=false)
rolllist(r :: Roll; generator=false)
```

サイコロ `d` またはロール `r` のすべての可能なロールリストを表示します。`DiceRoll` の場合、これはすべてのサイコロの結果のリストです。`CompositeRoll` やその部分が `Roll` で構成されている他の `Roll` の場合も同様です。
