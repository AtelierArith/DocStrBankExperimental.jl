```
termnames(term::AbstractTerm)
```

Return the name of the statistical variable associated with a term.

Return value is either a `String`, an iterable of `String`s or the empty vector  if there is no associated variable (e.g. `termnames(InterceptTerm{false}())`).
