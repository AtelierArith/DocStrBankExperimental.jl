```
rstar(rng=Random.GLOBAL_RNG, classifier, chains::Chains; kwargs...)
```

MCMC `chains`の$R^*$収束診断を`classifier`を用いて計算します。

ここでサポートされているキーワード引数は、サンプルの配列とチェインインデックスのための`rstar`と同じです。

# 例

```jldoctest rstar; setup = :(using Random; Random.seed!(200))
julia> using MLJBase, MLJDecisionTreeInterface, Statistics

julia> chains = Chains(fill(4.0, 100, 2, 3));
```

確率的分類器を用いて$R^*$統計量の分布を計算できます。

```jldoctest rstar
julia> distribution = rstar(DecisionTreeClassifier(), chains);

julia> isapprox(mean(distribution), 1; atol=0.1)
true
```

決定論的分類器の場合、単一の$R^*$統計量が返されます。

```jldoctest rstar
julia> decisiontree_deterministic = Pipeline(
           DecisionTreeClassifier();
           operation=predict_mode,
       );

julia> value = rstar(decisiontree_deterministic, chains);

julia> isapprox(value, 1; atol=0.2)
true
```
