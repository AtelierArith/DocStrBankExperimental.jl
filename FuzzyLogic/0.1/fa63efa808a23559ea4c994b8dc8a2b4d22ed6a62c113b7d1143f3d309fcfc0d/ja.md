```julia
struct EKMDefuzzifier <: FuzzyLogic.Type2Defuzzifier
```

タイプ2ファジィシステムのための強化されたカーニク-メンデル型縮小/デファジフィケーションアルゴリズム。

### パラメータ

  * `N::Int64`: 積分のためのサブインターバルの数、デフォルトは100。
  * `maxiter::Int64`: 最大反復回数、デフォルトは100。

# 拡張ヘルプ

このアルゴリズムは以下で紹介されました。

  * Wu, D. and J.M. Mendel, "Enhanced Karnik-Mendel algorithms," IEEE Transactions on Fuzzy Systems, vol. 17, pp. 923-934. (2009)
