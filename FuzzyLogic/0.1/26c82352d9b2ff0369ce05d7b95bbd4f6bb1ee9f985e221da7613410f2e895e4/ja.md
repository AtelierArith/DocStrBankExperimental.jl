```julia
struct IASCDefuzzifier <: FuzzyLogic.Type2Defuzzifier
```

タイプ2推論システムのためのデファジファイア、停止条件付き反復アルゴリズム（IASC）を使用。

### パラメータ

  * `N::Int64`: 積分のためのサブインターバルの数、デフォルトは100。

# 拡張ヘルプ

このアルゴリズムは以下で紹介されました。

  * Duran, K., H. Bernal, and M. Melgarejo, "Improved iterative algorithm for computing the generalized centroid of an interval type-2 fuzzy set," Annual Meeting of the North American Fuzzy Information Processing Society, pp. 190-194. (2008)
