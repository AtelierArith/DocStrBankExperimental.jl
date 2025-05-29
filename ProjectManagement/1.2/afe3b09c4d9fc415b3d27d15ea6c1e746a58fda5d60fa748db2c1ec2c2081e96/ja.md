```
density(proj::Project, nsamples=100_000, rng=Random.default_rng())
```

プロジェクトを完了するのにかかる時間の確率密度関数を表示しました。`nsamples`は分布を推定するために使用されるサンプルの数を制御し、これを増やすと時間がかかりますが、より正確になります。`rng`は使用する乱数生成器を制御し、通常はこれに触れる必要はありません。

[Gadfly.jl](https://github.com/GiovineItalia/Gadfly.jl)が表示に使用されています。また、[RecipesBase.jl](https://github.com/JuliaPlots/RecipesBase.jl)のレシピも提供されているため、[StatsPlots.jl](https://github.com/JuliaPlots/StatsPlots.jl)と同様に使用できます：`StatsPlots.density(proj)`として。
