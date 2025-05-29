```
maximal_order(O::AbsNumFieldOrder; index_divisors::Vector{ZZRingElem}, discriminant::ZZRingElem, ramified_primes::Vector{ZZRingElem}) -> AbsNumFieldOrder
```

Returns the maximal order of the number field that contains $O$. Additional information can be supplied if they are already known, as the ramified primes, the discriminant of the maximal order or a set of integers dividing the index of $O$ in the maximal order.
