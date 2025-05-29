```
MorisitaOverlap(q::Int)
```

Creates a MorisitaOverlap distance, a general, statistical measure of dispersion which can also be used on dictionaries such as created from q-grams. See https://en.wikipedia.org/wiki/Morisita%27s*overlap*index This is more fine-grained than many of the other QGramDistances since it is based on the counts per q-gram rather than only which q-grams are in the strings.

The distance corresponds to

$(2 * sum(m(s1) .* m(s2)) / (sum(m(s1).^2)*M(s2)/M(s1) + sum(m(s2).^2)*M(s1)/M(s2))$

where $m(s)$ is the vector of q-gram counts for string $s$ and $M(s)$ is the sum of those counts.
