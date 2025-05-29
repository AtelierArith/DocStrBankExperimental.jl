```
probability(grammar::AbstractGrammar, index::Int)::Real
```

文法のルールの確率を返します。可能な限り [`log_probability`](@ref) を使用してください。

!!! warning
    文法が確率的でない場合、警告が表示され、均一な確率が仮定されます。

