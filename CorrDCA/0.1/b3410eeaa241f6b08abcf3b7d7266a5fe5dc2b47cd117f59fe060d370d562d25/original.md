```
compute_weights(Z::Matrix{Ti}, theta::Real) where Ti <: Integer
```

Compute the normalized counts of the number of sequences at hamming distance ≤ `theta` from any given sequence  in `Z`.
