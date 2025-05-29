```
diff_inv(G::AbstractLieGroup, g, X)
diff_inv!(G::AbstractLieGroup, Y, g, X)
```

関数 $ι_{\mathcal G}(g) = g^{-1}$ の微分を計算します。ここで、$Dι_{\mathcal G}(g): \mathfrak g → \mathfrak g$ です。これは `Y` のインプレースで行うことができます。
