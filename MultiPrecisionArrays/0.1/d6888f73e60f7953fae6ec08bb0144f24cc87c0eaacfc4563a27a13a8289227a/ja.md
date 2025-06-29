mplu!(MPF::MPLFact,A::AbstractArray{TW,2}) where TW <: Real

新しい行列 A のためにストレージを再利用するために、マルチ精度因子分解 MPF を上書きします。

もちろん、これは元の因子分解を破壊します。

これを使用するには、次のようにします。

```
MPF=mplu!(MPF,A)
```

単に使用するだけでは

```
mplu!(MPF,A) # これをしないでください！
```

（つまり、明示的に MPF を返さずに）

あなたが望むことをしないかもしれません。なぜなら、マルチ精度因子分解構造は不変であり、MPF.AF.info は変更できないからです。

MPF を再割り当てすることは機能し、元の配列のほとんどすべてのストレージを再利用します。

この内容で静的配列を使用したい場合は、可変の @MArray コンストラクタを使用してください。
