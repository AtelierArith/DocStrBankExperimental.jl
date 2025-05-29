```julia
abstract type Planner
```

抽象プランナータイプ。構築されると、`planner`は`domain`、初期`state`、および`spec`で実行でき、[`Solution`](@ref)を返します。`state`と`spec`の代わりに`problem`を提供することもできます：

```
planner(domain::Domain, state::State, spec)
planner(domain::Domain, problem::Problem)
```

新しいプランナーは[`solve`](@ref)と（オプションで）[`refine!`](@ref)を定義する必要があります。
