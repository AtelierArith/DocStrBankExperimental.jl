```
diff_group_apply(A::GroupAction{T, L, M}, g, p, X)
diff_group_apply!(A::GroupAction{T, L, M}, Y, g, p, X)
```

Compute the differential $D_g σ_g(p): \mathfrak g → \mathfrak g$, where we use the short hand notation $σ_p(g) = σ(g,p)$ for a left action, and for a right action $σ_p(g) = σ(p, g)$.
