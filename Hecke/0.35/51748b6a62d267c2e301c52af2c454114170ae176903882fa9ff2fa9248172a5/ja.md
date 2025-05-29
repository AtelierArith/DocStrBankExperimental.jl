```
quo(G::FinGenAbGroup, n::Integer}) -> FinGenAbGroup, Map
quo(G::FinGenAbGroup, n::ZZRingElem}) -> FinGenAbGroup, Map
```

$$
H = G/nG
$$

の商と射影 $p : G \to H$ を返します。
