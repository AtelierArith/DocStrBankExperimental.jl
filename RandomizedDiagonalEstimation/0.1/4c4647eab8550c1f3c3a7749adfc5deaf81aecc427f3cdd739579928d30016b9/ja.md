```
function EstimateMoMDiagonal(A::Matrix{Float64},Algorithm::Symbol, StoppingCriterion::Symbol, distribution::Symbol, ngroups::Int, groupsize::Int, normalizationParam::Bool=true, parallelizationParam::Bool=false ;maxqueries::Int,O=nothing)
```

行列の対角線のランダム化推定を中央値の平均原理を使用して計算する関数

入力:

  * A: 対角線を推定する行列
  * Algorithm: 使用する対角線推定器を選択します。オプションは次のとおりです。

      * :GirardHutchinson
      * :DiagPP
      * :NysDiagPP
      * :XDiag
      * :XNysDiag
      * :GirardHutchinsonShift
      * :RSVD
      * :AdaptiveDiagPP
  * StoppingCriterion: 終了方法、可能なオプション

      * queries: Aへの最大クエリ数に達したときに終了

          * maxqueries: Aへの最大クエリ数
      * 将来的なバージョンで追加される可能性のあるさらなる停止基準に注意してください
  * distribution: ランダムベクトルが引き出される分布を選択します。組み込みのオプションは次のとおりです。

      * :Rademacher
      * :Gaussion
      * :custom、この場合、テストベクトルを列として持つ行列を提供します

          * O: テストベクトルを列として持つ行列
  * ngroups: 中央値の平均推定器のグループ数
  * groupsize: 中央値の平均推定器のグループサイズ
