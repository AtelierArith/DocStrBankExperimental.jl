```
function EstimateDiagonal(A::Matrix{Float64},Algorithm::Symbol, StoppingCriterion::Symbol, distribution::Symbol, normalizationParam::Bool=true, parallelizationParam::Bool=false ;maxqueries::Int=0,O=nothing,var_est::Float64=1/eps(),epsilon::Float64=1.0, delta::Float64=1.0,con::Float64=1.0)
```

行列 A の対角線のランダム化推定値を計算するためのメイン関数

入力:

  * A: 対角線を推定する行列
  * Algorithm: 使用する対角線推定器を選択します。オプションは次のとおりです。

      * :GirardHutchinson
      * DiagPP
      * :NysDiagPP
      * :XDiag
      * :GirardHutchinsonShift
      * :RSVD
      * :AdaptiveDiagPP
  * StoppingCriterion: 終了方法、可能なオプション

      * doubling: 倍増戦略を使用し、相対誤差推定が閾値 eps を下回ったときに終了します。必須パラメータ

          * queries_start: 開始時のクエリ数
          * eps: 相対誤差推定の境界
          * 注意: :GirardHutchinson と :DiagPP のみで実装されています。他の方法は今後のリリースで追加されます。
      * queries: A に対する最大クエリ数に達したときに終了します。

          * maxqueries: A に対する最大クエリ数
      * adaptive: :AdaptiveDiagPP を使用した epsilon delta 推定器

          * epsdelta: epsilon-delta 推定器のパラメータ (epsilon, delta)
          * maxiter: 最大反復回数
  * distribution: ランダムベクトルが引き出される分布を選択します。組み込みオプションは次のとおりです。

      * :Rademacher
      * :Gaussion
      * :custom, この場合、テストベクトルを列として持つ行列を提供します。

          * O: テストベクトルを列として持つ行列

```
