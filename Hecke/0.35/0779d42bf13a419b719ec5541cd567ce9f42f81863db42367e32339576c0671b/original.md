```
subfields(L::SimpleNumField) -> Vector{Tuple{NumField, Map}}
```

Given a simple extension $L/K$, returns all subfields of $L$ containing $K$ as tuples $(k, \iota)$ consisting of a simple extension $k$ and an embedding $\iota k \to K$.
