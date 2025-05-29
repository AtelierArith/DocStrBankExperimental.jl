```julia
hopf_normal_form(
    prob,
    br,
    ind_hopf;
    nev,
    verbose,
    lens,
    Teigvec,
    detailed,
    autodiff,
    scaleζ
)

```

ホップ正規形を計算します。

# 引数

  * `prob::AbstractBifurcationProblem` 分岐問題
  * `br` [`continuation`](@ref) への呼び出しからのブランチ結果
  * `ind_hopf` `br` における分岐点のインデックス
  * `options` ニュートンソルバーのオプション

# オプション引数

  * `nev = 5` スペクトル射影を推定するために計算する固有値の数
  * `verbose` 情報を印刷するためのブール値
  * `lens` パラメータ軸
  * `detailed = true` 簡略化された正規形を計算するかどうか
  * `Teigvec` 固有ベクトルのベクトルタイプ
  * `scaleζ = norm` 固有ベクトルを正規化するためのノルム

# 利用可能なメソッド

正規形 `hopfnf` が計算されたら、`predictor(hopfnf, ds)` を呼び出して分岐する周期軌道の推定を得ることができます。
