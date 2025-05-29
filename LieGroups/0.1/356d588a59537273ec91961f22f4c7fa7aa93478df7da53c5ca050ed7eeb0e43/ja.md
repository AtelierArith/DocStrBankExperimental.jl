```
diff_apply(A::GroupAction{T, L, M}, g, p, X)
diff_apply!(A::GroupAction{T, L, M}, Y, g, p, X)
```

微分 $D_p σ_g(p): T_p\mathcal M → T_{σ_g(p)}\mathcal M$ を計算します。左群作用の場合、$σ_g(p) = σ(g,p)$ となり、右作用の場合は $σ_g(p) = σ(p, g)$ となります。
