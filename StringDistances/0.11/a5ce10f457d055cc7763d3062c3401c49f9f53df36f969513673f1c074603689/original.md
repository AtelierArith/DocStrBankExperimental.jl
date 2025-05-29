```
Jaccard(q::Int)
```

Creates a Jaccard distance.

The distance corresponds to 

$1 - |Q(s1, q) ∩ Q(s2, q)| / |Q(s1, q) ∪ Q(s2, q))|$

where $Q(s, q)$  denotes the set of q-grams of length n for the string s
