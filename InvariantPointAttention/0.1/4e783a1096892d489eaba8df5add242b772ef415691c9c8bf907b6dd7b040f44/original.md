```
softmax1(x, dims = 1)
```

Behaves like softmax, but as though there was an additional logit of zero along dims (which is excluded from the output). So the values will sum to a value between zero and 1.

See https://www.evanmiller.org/attention-is-off-by-one.html
