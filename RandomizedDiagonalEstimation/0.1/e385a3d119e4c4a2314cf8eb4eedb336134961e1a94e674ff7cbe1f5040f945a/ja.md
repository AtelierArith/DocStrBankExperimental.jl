```
function EstimateFunctionDiagonal(A::Matrix{Float64},fmat,f,Algorithm::Symbol, StoppingCriterion::Symbol, distribution::Symbol, MatFuncApprox::Symbol, deg::Int64, normalizationParam::Bool=true;maxqueries::Int,int::Tuple=(0.0,1.0),q=4,O=nothing)
```

行列関数の対角線のランダム推定を計算するためのメイン関数

入力:

  * A: 関数の入力としての行列
  * f: 対角線を近似する関数
  * Algorithm: 使用する対角線推定器を選択します。オプションは次のとおりです。

      * :GirardHutchinson
      * :funDiagPP
      * :funNys
  * MatFuncApprox: f(A)bを近似する方法

      * Chebshev: チェビシェフ多項式を使用

          * 区間intと次数degが必要
      * Remez: レメズ多項式を使用

          * 区間intと次数degが必要
      * Krylov: アーノルディ近似を使用

          * Krylov部分空間におけるAの最大次数をdegで示す必要があります
      * CG: 逆行列の対角線を近似するために共役勾配法を使用します。注意: fは無視されます

          * Krylov部分空間におけるAの最大次数をdegで示す必要があります
  * StoppingCriterion: 終了方法、可能なオプション

      * queries: Aへの最大クエリ数に達したときに終了します

          * maxqueries: Aへの最大クエリ数
  * distribution: ランダムベクトルが引き出される分布を選択します。組み込みオプションは次のとおりです。

      * :Rademacher
      * :Gaussion
      * :custom、この場合、テストベクトルを列として持つ行列を提供します

          * O: テストベクトルを列として持つ行列
  * deg: 多項式の次数またはKrylov部分空間におけるAの最大次数、MatFuncApproxに応じて

```
