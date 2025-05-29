```
logitsample([rng], logits, [buffer=similar(logits)]) -> Int
```

Sample an index from a logit distribution using the Gumbel argmax trick.

Alternatively pass a buffer to avoid allocating a new array when creating the random numbers.
