```
michalewicz(x; m=10)
```

The **Michalewicz** function is a $d$-dimensional function with several steep valleys, where `m` controls the steepness. `m` is usually set at 10. For 2 dimensions, $x^* = [2.20, 1.57]$, with $f(x^*) = -1.8011$.

$$
f(x) = -\sum_{i=1}^{d}\sin(x_i) \sin^{2m}\left(\frac{ix_i^2}{\pi}\right)
$$
