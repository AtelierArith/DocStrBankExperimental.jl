```julia
hopf_normal_form(prob, pt, ls; verbose, autodiff, L)

```

ホップ標準形を計算します。

# 引数

  * `prob::AbstractBifurcationProblem` 分岐問題
  * `pt::Hopf` ホップ分岐点
  * `ls` 線形ソルバー

# オプション引数

  * `verbose` 情報を印刷するためのブール値
  * `L` ヤコビ行列
