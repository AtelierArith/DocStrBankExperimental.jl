```
SPATest(rejH0::Int, mu_u::Vector{Float64}, mu_c::Vector{Float64}, mu_l::Vector{Float64}, pvalue_u::Float64, pvalue_c::Float64, pvalue_l::Float64, pvalue::Float64, teststat::Float64)
```

Hansen (2005) の「A Test for Superior Predictive Ability」で提案されたSPAテストの出力タイプ。このタイプのフィールド名は参照された論文に従っているため、詳細についてはその論文を参照してください。このタイプのフィールドは次のとおりです：

```
rejH0 <- 帰無仮説が棄却される場合はtrue、そうでない場合はfalse
mu_u <- 閾値率の上限に関連するmu
mu_c <- 推奨されるmu
mu_l <- 閾値率の下限に関連するmu
pvalue_u <- mu_uに関連するp値
pvalue_c <- mu_cに関連するp値
pvalue_l <- mu_lに関連するp値
pvalueauto <- 推奨されるp値（通常はpvalue_c、ただしこの方法が失敗する稀な状況を除く）
teststat::Float64 <- SPAテスト統計量（ソース論文のtSPAを参照）
```

異なるmu変数、{u, c, l}は、参照された記事のp370-371で説明されています。

ほとんどのユーザーはフィールドpvalueautoに興味があるでしょう。
