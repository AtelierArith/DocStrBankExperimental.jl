```
diff_apply(A::GroupAction{T, L, M}, g, p, X)
diff_apply!(A::GroupAction{T, L, M}, Y, g, p, X)
```

Compute the differential $D_p σ_g(p): T_p\mathcal M → T_{σ_g(p)}\mathcal M$, where for a left group action we have $σ_g(p) = σ(g,p)$, for a right action $σ_g(p) = σ(p, g)$.
