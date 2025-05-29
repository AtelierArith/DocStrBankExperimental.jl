```
ace_high(bit::Bool)::Bool
```

Determine if aces are highest value cards in a deck. After `ace_high(true)` aces are greater than kings. After `ace_high(false)`, aces are lower than twos. This affects the result of `<` comparisons and sorting.

```
ace_high()::Bool
```

Return the current status of aces (`true` means aces are high, `false` means aces are low).
