```
OrderedBeta(μ, ϕ, k0, k1)
```

この分布は、心理科学で一般的に観察されるデータ（スライダー尺度からのデータなど）を記述するための適切で簡潔な方法として、[Kubinec (2023)](https://doi.org/10.1017/pan.2022.20) によって導入されました。これは、0と1の間の区間 ]0, 1[ におけるベータ分布に、0と1での追加の点質量を持つように定義されています。ベータ分布は、[`BetaPhi2`](@ref) パラメータ化を使用して指定されます。

# 引数

  * `μ`: スケール 0-1 の位置パラメータ
  * `ϕ`: 精度パラメータ（正でなければなりません）。このパラメータは、従来のベータ分布の精度の半分に相当する、ベータ分布の[`BetaPhi2`](@ref) 再パラメータ化に基づいていることに注意してください。例えば、`ordbetareg` パッケージで実装されています。
  * `k0`: ゼロの確率が増加する最初のカットポイント。おそらく 0.5 より低い（ordbetareg では `cutzero` と呼ばれ、論文では *k1* と呼ばれています）。
  * `k1`: 1 の確率が増加する2番目のカットポイント。おそらく 0.5 より高い。`k0` より大きくなければなりません（ordbetareg では `cutone` と呼ばれ、論文では *k2* と呼ばれています）。

`k0=0` および `k1=1` の場合、この分布はベータ分布に相当します（すなわち、ゼロや1は存在しません）。

# 詳細

![](https://github.com/DominiqueMakowski/SubjectiveScalesModels.jl/blob/main/docs/img/animation_OrderedBeta.gif?raw=true)

上の図は、*k0* と *k1* のパラメータ空間を示しており、ゼロと1の大きな割合を生成する領域（赤色）を示しています。これを理解することは、これらのパラメータに適切な事前分布を設定するために重要です。

`ordbetareg` R パッケージと比較して、主な違いは次のとおりです：

  * *phi* ϕ (Julia バージョン) = *phi* ϕ (R バージョン) / 2
  * *k0* と *k1* は、原始スケール [0, 1] で指定され、独立しています（R パッケージでは、ロジットスケールで指定され、k1 は k0 からの差として表現されます）。

# 例

```jldoctest
julia> OrderedBeta(0.5, 1, 0.1, 0.9)
OrderedBeta{Float64}(μ=0.5, ϕ=1.0, k0=0.1, k1=0.9)
```

# 参考文献

  * Kubinec, R. (2023). Ordered beta regression: a parsimonious, well-fitting model for continuous data with lower and upper bounds. Political analysis, 31(4), 519-536.
