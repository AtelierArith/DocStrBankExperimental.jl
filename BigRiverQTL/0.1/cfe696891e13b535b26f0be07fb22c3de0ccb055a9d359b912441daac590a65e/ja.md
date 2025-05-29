```
kinship_lin(mat,cross)
```

線形カーネルによって親族関係（または気候的関連性、[`kinship_gs`](@ref)）行列を計算します。

# 引数

  * `mat` : 通常、[R/qtl](https://rqtl.org/tutorials/rqtltour.pdf)、[R/qtl2](https://kbroman.org/qtl2/assets/vignettes/user_guide.html) またはそれに相当するパッケージから抽出された遺伝子型（またはアレル）確率の行列。サイズ(mat)= (p,n) は p 遺伝子マーカー x n 個体です。
  * `cross` : 遺伝子マーカーにおけるアレルまたは遺伝子型のインスタンスを示すスカラー。例：遺伝子型の場合は 1（0,1,2 とラベル付け）、RIF の場合は 2、四方交配の場合は 4、HS マウス（アレル確率）の場合は 8 など。

# 出力

対角線上に 1 が含まれる n x n 対称（正定値）行列を返します。

遺伝子型データについては、[`kinshipCtr`](@ref)、[`kinshipStd`](@ref) も参照してください。
