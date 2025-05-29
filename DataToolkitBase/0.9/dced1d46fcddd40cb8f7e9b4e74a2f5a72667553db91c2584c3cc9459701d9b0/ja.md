利用可能なプラグインから得られた `Advices` のコレクション。

個々の `Advices` と同様に、`AdviceAmalgamation` も関数として呼び出すことができます。ただし、次の便利な構文もサポートしています：

```
(::AdviceAmalgamation)(f::Function, args...; kargs...) # -> result
```

# コンストラクタ

```
AdviceAmalgamation(adviseall::Function, advisors::Vector{Advice},
                   plugins_wanted::Vector{String}, plugins_used::Vector{String})
AdviceAmalgamation(plugins::Vector{String})
AdviceAmalgamation(collection::DataCollection)
```
