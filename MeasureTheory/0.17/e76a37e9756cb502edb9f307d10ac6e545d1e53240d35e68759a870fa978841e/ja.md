```
@parameterized <declaration>
```

<declaration>は測度とそのデフォルトパラメータを提供し、基準測度との関係を指定します。例えば、@parameterized Normal(μ,σ)は`Normal`がデフォルトパラメータ`μ`と`σ`を持つ測度であることを宣言します。結果は次のように等価です。

```
struct Normal{N,T} <: ParameterizedMeasure{N}
    par :: NamedTuple{N,T}
end
KeywordCalls.@kwstruct Normal(μ,σ)
Normal(μ,σ) = Normal((μ=μ, σ=σ))
```

`@kwstruct`の詳細については[KeywordCalls.jl](https://github.com/cscherrer/KeywordCalls.jl)を参照してください。
