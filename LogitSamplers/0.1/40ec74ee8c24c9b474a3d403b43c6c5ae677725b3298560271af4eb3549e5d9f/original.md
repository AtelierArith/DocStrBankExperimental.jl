```
Top_nσ(n)
```

A logit transform that masks out logits below `n` standard deviations of the maximum logit.

Top-nσ is temperature-invariant, i.e. the candidate set does not change with temperature.

See: https://arxiv.org/pdf/2411.07641
