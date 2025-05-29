A bilevel linear optimization problem of the form:

```
min cx^T * x + cy^T * y
s.t. G x + H y <= q
     x_j ∈ [xl_j,xu_j]
     x_j ∈ ℤ ∀ j ∈ Jx
     y ∈ arg min {
        d^T * y + x^T * F * y
        s.t. A x + B y <= b
             y_j ∈ [yl_j,yu_j]
        }
```

Note that integer variables are allowed at the upper level.
