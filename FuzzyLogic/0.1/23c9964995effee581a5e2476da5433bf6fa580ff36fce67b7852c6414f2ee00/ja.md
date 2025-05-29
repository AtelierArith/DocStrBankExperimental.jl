```julia
struct EIASCDefuzzifier <: FuzzyLogic.Type2Defuzzifier
```

IASCを用いたタイプ2推論システムのためのデファズィファイア。

### パラメータ

  * `N::Int64`: 積分のためのサブインターバルの数、デフォルトは100。

# 拡張ヘルプ

このアルゴリズムは以下で紹介されました。

  * Wu, D. and M. Nie, "Comparison and practical implementations of type-reduction algorithms for type-2 fuzzy sets and systems," Proceedings of FUZZ-IEEE, pp. 2131-2138 (2011)
