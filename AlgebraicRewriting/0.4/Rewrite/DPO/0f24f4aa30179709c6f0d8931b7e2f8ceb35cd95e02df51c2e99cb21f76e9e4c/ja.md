```
rewrite_match_maps(r::Rule{:DPO}, m)
```

ACSetに対してDPO書き換えルール（スパンとして与えられる、L<-I->R）を適用し、書き換えを適用する場所を示すマッチモルフィズム`m`を使用します。               l   r            L <- I -> R          m ↓    ↓    ↓            G <- K -> H

これは`pushout_complement`と`pushout`を実装する任意の型で機能します。
