```
quo(G::FinGenAbGroup, n::Integer}) -> FinGenAbGroup, Map
quo(G::FinGenAbGroup, n::ZZRingElem}) -> FinGenAbGroup, Map
```

剰余 $H = G/nG$ と射影 $p : G \to H$ を返します。
