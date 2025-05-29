```
fourvelfromcoordvel(u)
```

Compute a properly normalized velocity vector from the coordinate velocity $u$, given as a 3-vector.  This gives a correct result for tachyons but will diverge (result can contain `Inf` or `NaN`) for null vectors.
