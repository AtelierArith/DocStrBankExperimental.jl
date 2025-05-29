```
atomic_weight[elm::Element]::Union{NumberInterval, UncertainValue}
```

Atomic weights from the 2020 tabulation at https://ciaaw.org/atomic-weights.htm.  Not all elements are represented because not all  elements have a nominal isotopic distribution.  Some, like Tc, don't exist in nature.  Others, like Pm, are instable.  Most atomic weights are given as `UncertainValue` instances while a few are `NumberInterval` instances.  For example, the atomic weight of Pb is highly variable and is thus given as a range.  (See the website for more details.)
