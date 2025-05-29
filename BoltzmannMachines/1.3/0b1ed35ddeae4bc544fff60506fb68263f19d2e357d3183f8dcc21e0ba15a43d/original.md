```
aislogimpweights(rbm1, rbm2; ...)
```

Computes the logarithmised importance weights for estimating the log-ratio log(Z2/Z1) for the partition functions Z1 and Z2 of `rbm1` and `rbm2`, respectively. Implements the procedure described in section 4.1.2 of [Salakhutdinov, 2008]. This requires that `rbm1` and `rbm2` are of the same type and have the same number of visible units.
