```
TermSet <: AbstractSet{AbstractTerm}
```

Wrapped `Set{AbstractTerm}` that specifies a collection of terms. Commonly used methods for `Set` work in the same way for `TermSet`.

Compared with `StatsModels.TermOrTerms`, it does not maintain order of terms but is more suitable for dynamically constructed terms.
