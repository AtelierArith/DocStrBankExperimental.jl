```
ProbBackwardPlanner(;
    search_noise::Float64 = 1.0,
    kwargs...
)
```

同じノード拡張ルールを持つ逆方向探索の確率的バリアントで、[`ProbForwardPlanner`](@ref)と同様です。

`BackwardPlanner{Float64}`のエイリアスです。他の引数については[`BackwardPlanner`](@ref)を参照してください。
