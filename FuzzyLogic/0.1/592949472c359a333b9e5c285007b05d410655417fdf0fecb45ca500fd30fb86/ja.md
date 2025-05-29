```julia
struct KarnikMendelDefuzzifier <: FuzzyLogic.Type2Defuzzifier
```

Karnik-Mendel型の縮約/デファジフィケーションアルゴリズムは、タイプ2ファジィシステム用です。

### パラメータ

  * `N::Int64`: 積分のためのサブインターバルの数、デフォルトは100。
  * `maxiter::Int64`: 最大反復回数、デフォルトは100。
  * `atol::Float64`: 反復停止のための絶対許容誤差

# 拡張ヘルプ

このアルゴリズムは以下で紹介されました。

  * Karnik, Nilesh N., and Jerry M. Mendel. ‘Centroid of a Type-2 Fuzzy Set’. Information Sciences 132, no. 1–4 (February 2001): 195–220
