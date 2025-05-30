```
test_covariate_adjustment(g, X, Y, S)
```

Check if `S` is a covariate adjustment set relative to `(X, Y)` in graph `g`. 

Based on the sound and complete graphical criterion for covariate adjustment given in https://arxiv.org/abs/1203.3515 using the algorithmic approach proposed in https://arxiv.org/abs/1803.00116. Output is a boolean.
