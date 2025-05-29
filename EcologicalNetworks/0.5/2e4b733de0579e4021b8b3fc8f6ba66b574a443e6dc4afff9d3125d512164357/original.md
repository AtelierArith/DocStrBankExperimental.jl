```
conditional_entropy(P::AbstractArray, given::I)
```

Computes the conditional entropy of probability matrix. If `given = 1`, it is the entropy of the columns, and vise versa when `given = 2`. Output in bits.

Does not check whether `P` is a valid probability matrix.
