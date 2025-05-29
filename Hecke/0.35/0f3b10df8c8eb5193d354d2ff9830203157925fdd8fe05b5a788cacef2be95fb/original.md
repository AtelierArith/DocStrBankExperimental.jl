```
primary_decomposition(I::AlgAssAbsOrdIdl [O::Order]) -> Vector{Tuple}
```

Return the primary decomposition of $I$ over the order $O$ as a list of tuples $(P, Q)$ where $P$ is prime $Q$ is $P$-primary and $I$ is the product of the $Q$.

The rational span of $O$ must be etale and if no order is specified, the left order of $I$ is used.
