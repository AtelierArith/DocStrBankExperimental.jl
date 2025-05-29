```
diff_group_apply(A::GroupAction{T, L, M}, g, p, X)
diff_group_apply!(A::GroupAction{T, L, M}, Y, g, p, X)
```

微分 $D_g σ_g(p): \mathfrak g → \mathfrak g$ を計算します。ここで、左作用の場合は短縮表記 $σ_p(g) = σ(g,p)$ を使用し、右作用の場合は $σ_p(g) = σ(p, g)$ を使用します。
