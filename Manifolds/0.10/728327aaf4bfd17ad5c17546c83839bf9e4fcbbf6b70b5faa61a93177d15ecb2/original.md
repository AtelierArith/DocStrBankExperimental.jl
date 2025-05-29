```
apply(A::AbstractGroupAction, a, p)
```

Apply action `a` to the point `p` using map $τ_a$, specified by `A`. Unless otherwise specified, the right action is defined in terms of the left action:

$$
\mathrm{R}_a = \mathrm{L}_{a^{-1}}
$$
