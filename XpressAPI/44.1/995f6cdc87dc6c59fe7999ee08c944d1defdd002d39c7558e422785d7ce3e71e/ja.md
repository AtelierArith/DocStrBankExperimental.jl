```
XPRSgetqrowqmatrix(prob, row, start, colind, rowqcoef, maxcoefs, first, last)::start, colind, rowqcoef, ncoefs
```

与えられた範囲内の列に対する二次制約係数行列の非ゼロ要素を返します。

最大の効率を達成するために、`XPRSgetqrowqmatrix`はこの行列の下三角部分のみを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 二次係数を返す行のインデックス。
  * `start::AbstractVector{Int32}`: 各要求された列の`colind`および`rowqcoef`配列内の開始オフセットを示すインデックスで埋められる整数配列。
  * `colind::AbstractVector{Int32}`: Qの下三角部分の非ゼロ要素の列インデックスで埋められる長さmaxcoefsの整数配列。
  * `rowqcoef::AbstractVector{Float64}`: 非ゼロ要素の値で埋められる長さmaxcoefsの倍精度配列。
  * `maxcoefs::Integer`: colindおよびrowqcoefに保存される要素の数。
  * `first::Integer`: 範囲内の最初の列。
  * `last::Integer`: 範囲内の最後の列。

# 戻り値

  * `start::AbstractVector{Int32}`: 各要求された列の`colind`および`rowqcoef`配列内の開始オフセットを示すインデックスで埋められる整数配列。
  * `colind::AbstractVector{Int32}`: Qの下三角部分の非ゼロ要素の列インデックスで埋められる長さmaxcoefsの整数配列。
  * `rowqcoef::AbstractVector{Float64}`: 非ゼロ要素の値で埋められる長さmaxcoefsの倍精度配列。
  * `ncoefs::Int32`: 問い合わせた列の非ゼロ要素の数が返される整数へのポインタ。

C APIの対応する関数のドキュメントも参照してください [XPRSgetqrowqmatrix](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqrowqmatrix.html)。
