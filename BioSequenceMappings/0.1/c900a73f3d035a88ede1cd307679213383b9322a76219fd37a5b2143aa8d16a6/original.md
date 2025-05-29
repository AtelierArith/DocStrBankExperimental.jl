```
eachsequence(X::AbstractAlignment[, indices]; skip)
```

Return an iterator over the sequences in `X`. If `indices` is specified, consider only sequences at the corresponding indices. Use the integer argument `skip` to return only one sequence every `skip` (~ `1:skip:end`).
