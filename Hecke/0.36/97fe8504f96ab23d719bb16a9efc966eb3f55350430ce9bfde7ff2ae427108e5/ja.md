```
sunit_group(S::Vector{ZZRingElem}) -> FinGenAbGroup, Map
sunit_group(S::Vector{Integer}) -> FinGenAbGroup, Map
```

$$
S
$$

でサポートされる$Z$の$S$-ユニット群：$S$の素数でのみ割り切れる有理数の群。2番目の返り値は、群の要素を有理数に、または有理数を群の要素に戻すマップです。
