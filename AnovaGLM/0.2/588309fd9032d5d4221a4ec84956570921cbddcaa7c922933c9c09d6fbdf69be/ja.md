```
anova_lm(X, y; test::Type{<: GoodnessOfFit} = FTest, <keyword arguments>) 

anova_lm(test::Type{<: GoodnessOfFit}, X, y; <keyword arguments>)

anova(test::Type{<: GoodnessOfFit}, ::Type{LinearModel}, X, y; 
    type::Int = 1, 
    <keyword arguments>)
```

単純線形回帰のためのANOVA。

# 引数

  * `X` と `y` は `Matrix` と `Vector` または `Formula` と `Tables.jl` 互換のデータであることができます。
  * `test`: 適合度のための検定統計量。

# キーワード引数

  * `test`: 適合度のための検定統計量。
  * `type` はanovaのタイプを指定します（1、2、または3）。デフォルト値は1です。
  * `dropcollinear` は、`lm` がフルランク未満のモデル行列を受け入れるかどうかを制御します。true（デフォルト）の場合、線形依存列の各セットの最初のもののみが使用されます。冗長な線形依存列の係数は0.0であり、関連するすべての統計はNaNに設定されます。

`anova_lm` は `TableRegressionModel` オブジェクトを生成し、これは `lm` によってフィッティングされます。
