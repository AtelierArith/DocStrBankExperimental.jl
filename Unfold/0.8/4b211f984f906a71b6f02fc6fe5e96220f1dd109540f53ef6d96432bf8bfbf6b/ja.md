```
effects(design::AbstractDict, model::UnfoldModel; typical = mean)
```

`design`内のすべての項の組み合わせに対する限界効果を計算します。

Effects.jlパッケージに基づいて実装されています。UnfoldEffects.jlに再パッケージ化することができるかもしれません。誰かやってみませんか？これにより、Effects.jlパッケージの変更やバグ修正に対してクロスメンテナンスが容易になります。`design`は、評価したい予測因子（キー）とそのレベル（値）を含む辞書です。`typical`は、辞書に指定されていない他の予測因子が取るべき値を指します。

MixedModelsの場合、返される効果は「典型的」な被験者に基づいており、すべてのランダム効果は0に設定されます。

# 例

```julia-repl
 julia> f = @formula 0 ~ categoricalA + continuousA + continuousB
 julia> uf = fit(UnfoldModel, (Any => (f, times)), data, events)
 julia> d = Dict(:categorical => ["levelA", "levelB"], :continuous => [-2, 0, 2])
 julia> effects(d, uf)
```

は6つの予測値を生成します：A/-2, A/0, A/2, B/-2, B/0, B/2。
