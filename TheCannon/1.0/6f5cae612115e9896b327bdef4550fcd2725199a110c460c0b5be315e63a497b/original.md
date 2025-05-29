```
expand_labels(labels; quadratic=true)
```

If `labels` is a `Vector`, return it's quadratic (or linear) expansion. If `labels` is a `Matrix`, return the matrix whose rows are expansions of the rows of `labels`.

This is the transformation referred to as $\eta$ in Wheeler+ 2020, and as the "vectorizing function" in [Casey+ 2016](https://arxiv.org/abs/1603.03040).
