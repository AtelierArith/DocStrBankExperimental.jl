```
sunit_group_fac_elem(S::Vector{ZZRingElem}) -> FinGenAbGroup, Map
sunit_group_fac_elem(S::Vector{Integer}) -> FinGenAbGroup, Map
```

The $S$-unit group of $Z$ supported at $S$: the group of rational numbers divisible only by primes in $S$. The second return value is the map mapping group elements to rationals in factored form or rationals back to group elements.
