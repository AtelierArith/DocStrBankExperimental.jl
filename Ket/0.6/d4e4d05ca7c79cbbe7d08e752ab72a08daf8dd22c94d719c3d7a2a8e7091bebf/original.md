```
symmetric_isometry(dim::Integer, n::Integer)
```

Computes an isometry that encodes the symmetric subspace of `n` copies of a `dim`-dimensional space. Specifically, it maps a vector space of dimension `binomial(n + dim -1, dim -1)` onto the symmetric subspace of the symmetric subspace of the vector space of dimension `dim^n`.

Reference: [Watrous' book](https://cs.uwaterloo.ca/~watrous/TQI/), Sec. 7.1.1
