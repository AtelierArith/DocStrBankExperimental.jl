```
cycle(f::QuadBin{ZZRingElem}; proper::Bool = false) -> Vector{QuadBin{ZZRingElem}}
```

Return the cycle of `f` as defined by Buchmann–Vollmer (Algorithm 6.1). The cycle consists of all reduced, equivalent forms `g`, such that first coefficient of `f` and `g` have the same sign. The proper cycle consists of all equivalent forms, and has either the same or twice the size of the cycle. In the latter case, the cycle has odd length.
