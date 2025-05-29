```
values, frequency = histogram(dice; normalize=false)
values, frequency = histogram(roll; normalize=false)
```

Computes the histogram of a dice or roll. This operation can be intensive because it computes the histogram of its internal parts recursively, so it can slow for complicated rolls.
