```
orelse(a, b)  # overload this
⊘(a, b)  # alias \oslash
orelse(a, b, c, d, ...)  # using orelse(a, b) internally
```

Implements an alternative logic, like having two options a and b, taking the first valid one. We decided for "orelse" instead of "alternatives" to highlight the intrinsic asymmetry in choosing.

The operator ⊘ (\oslash) is choosen to have an infix operator which is similar to \oplus, however clearly distinguishable, asymmetric, and somehow capturing a choice semantics. The slash actually is used to indicate choice (at least in some languages, like German), and luckily \oslash exists (and is not called \odiv).  
