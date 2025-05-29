```
 kinship_4way(genmat::Array{Float64,2})
```

異なるアレルをカウントする四方向交配データの親族関係を計算します：例 AB-AB=0; AB-AC=1; AB-CD=2,$\dots$ 注意：[R/qtl](https://cran.r-project.org/web/packages/qtl/qtl.pdf)では、遺伝子型は関数`read.cross`によって1=AC; 2=BC; 3=AD; 4=BDとしてラベル付けされています。

# 引数

  * `genmat` : `four-way cross`の遺伝子型の行列 $(1,2, \dots)$。          size(genematrix)= (p,n)、ここで`p`は遺伝子マーカーの数、`n`は個体（または系統）の数です。

# 出力

対角線上に1が含まれるn x nの対称行列を返します。
