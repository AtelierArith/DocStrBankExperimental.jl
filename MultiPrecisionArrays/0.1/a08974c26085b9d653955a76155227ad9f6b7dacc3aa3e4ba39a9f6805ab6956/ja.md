mpblu!(MPG::MPBFact, A::AbstractArray{TW,2}) where TW <: Real 新しい行列 A のためにストレージを再利用して多倍長因子分解 MPF を上書きします。

もちろん、これは元の因子分解を破壊します。

これを使用するには

```
MPG=mpblu!(MPF,A)
```

単に

```
mpblu!(MPF,A) # これはしないでください。
```

（つまり、明示的に MPG を返さずに）

あなたが望むことをしないかもしれません。なぜなら、多倍長因子分解構造は不変であり、MPF.AF.info は変更できないからです。

MPG を再割り当てすることは機能し、元の配列のほとんどすべてのストレージを再利用します。
