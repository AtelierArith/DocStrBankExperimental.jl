```
isgraphical(degs)
```

Return true if the degree sequence `degs` is graphical. A sequence of integers is called graphical, if there exists a graph where the degrees of its vertices form that same sequence.

### Performance

Time complexity: $\mathcal{O}(|degs|*\log(|degs|))$.

### Implementation Notes

According to Erdös-Gallai theorem, a degree sequence $\{d_1, ...,d_n\}$ (sorted in descending order) is graphic iff the sum of vertex degrees is even and the sequence obeys the property -

$$
\sum_{i=1}^{r} d_i \leq r(r-1) + \sum_{i=r+1}^n min(r,d_i)
$$

for each integer r <= n-1
