```
cut!(list,idx)
```

Cut the deck `list` by moving cards `1` through `idx` (inclusive) to the back of the deck so the first card now was formerly the one at position `idx+1`.

```
cut!(list)
```

Cut the deck at a random location. If the deck has `n` cards, then the cut location is given by the binomial random variable `B(n,1/2)`.
