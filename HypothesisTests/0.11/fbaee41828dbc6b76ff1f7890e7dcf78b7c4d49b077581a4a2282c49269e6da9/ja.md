```
OneWayANOVATest(groups)
OneWayANOVATest(groups::AbstractVector{<:Real}...)
```

`groups` の平均が等しいという仮説の一元配置分散分析テストを実行します。

一元配置分散分析（one-way ANOVA）は、2つ以上のサンプルの平均を比較するために使用できる手法です。ANOVAは、すべてのグループのサンプルが同じ平均値を持つ母集団から抽出されているという帰無仮説を検定します。これを行うために、母集団の分散の2つの推定値が作成されます。ANOVAは、平均間の分散とサンプル内の分散の比率であるF統計量を生成します。

実装: [`pvalue`](@ref)

# 外部リンク

  * [一元配置分散分析 - Wikipedia](https://en.wikipedia.org/wiki/One-way_analysis_of_variance)
