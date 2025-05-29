```
orthogonal(X::AbstractMatrix{<:Real})
```

Produce a parameter whose `value` is constrained to be an orthogonal matrix. The argument `X` need not be orthogonal.

This functionality projects `X` onto the nearest element subspace of orthogonal matrices (in Frobenius norm) and is overparametrised as a consequence.

Originally used in varz: https://github.com/wesselb/varz/blob/master/varz/vars.py#L446
