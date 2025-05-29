```
Disjunction(criteria...)
```

An early stopping criterion for loss-reporting iterative algorithms. 

Combines the specified stopping `criteria` dijunctively: if any one of the criteria applies, then stop.

**Syntactic sugar.** `c1 + c2 + ...` is equivalent to   `Disjunction(c1, c2, ...)`.
