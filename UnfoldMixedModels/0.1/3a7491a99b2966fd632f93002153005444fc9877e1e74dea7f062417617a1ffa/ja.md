```julia
pvalue(lrtvec)

```

Unfold-Method: 尤度比検定のp値を返します。通常は次のように計算されます：

# 例

julia> pvalue(likelihoodratiotest(m1,m2))

ここで、m1/m2はUnfoldLinearMixedModelです。

ヒント：2つのモデルのみを比較する場合、p値のベクトルを簡単に取得できます：

julia> vcat(pvalues(likelihoodratiotest(m1,m2))...)

複数のチャネルが現在線形化されて返されます。LRT後のチャネル数にアクセスできないため、次のようにできます：

julia> reshape(vcat(pvalues(likelihoodratiotest(m1,m2))...),ntimes,nchan)' 
