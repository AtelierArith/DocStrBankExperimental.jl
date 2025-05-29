```
sunit_group_fac_elem(S::Vector{ZZRingElem}) -> FinGenAbGroup, Map
sunit_group_fac_elem(S::Vector{Integer}) -> FinGenAbGroup, Map
```

$$
S
$$

でサポートされる$Z$の$S$-ユニット群：$S$の素数でのみ割り切れる有理数の群。2番目の返り値は、群の要素を因数分解された形の有理数にマッピングするマップ、または有理数を群の要素に戻すマップです。
