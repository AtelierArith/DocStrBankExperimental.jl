```
sunit_group(S::Vector{ZZRingElem}) -> FinGenAbGroup, Map
sunit_group(S::Vector{Integer}) -> FinGenAbGroup, Map
```

The $S$-unit group of $Z$ supported at $S$: the group of rational numbers divisible only by primes in $S$. The second return value is the map mapping group elements to rationals or rationals back to group elements.
