```
diff_inv(G::LieGroup{𝔽,AdditionGroupOperation}, g, X)
diff_inv!(G::LieGroup{𝔽,AdditionGroupOperation}, Y, g, X)
```

逆演算の微分を計算します $ι_{\mathcal G}(g) = g^-1 = -g$。これは[`AdditionGroupOperation`](@ref)の場合、$Dι_{\mathcal G}(g)[X] = -X$に簡略化されます。
