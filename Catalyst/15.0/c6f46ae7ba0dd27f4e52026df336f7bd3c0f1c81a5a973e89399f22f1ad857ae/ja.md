```
laplacianmat(rn::ReactionSystem, pmap=Dict(); sparse=false)
```

反応ネットワークのグラフラプラシアンの負を返します。化学反応ネットワークのODEシステムは、$\frac{dx}{dt} = Y A_k Φ(x)$として因数分解できます。ここで、$Y$は[`complexstoichmat`](@ref)であり、$A_k$はグラフラプラシアンの負であり、$Φ$は[`massactionvector`](@ref)です。$A_k$はn-by-n行列で、nは複合体の数であり、$A_{ij} = k_{ij}$は2つの複合体の間に反応が存在する場合、そうでない場合は0です。

デフォルトでは記号行列を返しますが、pmapを介してパラメータ値が指定されている場合は数値行列を返します。

**警告**: 他のCatalyst関数とは異なり、`laplacianmat`関数は記号的な場合に`Matrix{Num}`を返します。これはODEの行列分解の計算を容易にし、行列のスパース形式の乗算が機能することを保証するためです。
