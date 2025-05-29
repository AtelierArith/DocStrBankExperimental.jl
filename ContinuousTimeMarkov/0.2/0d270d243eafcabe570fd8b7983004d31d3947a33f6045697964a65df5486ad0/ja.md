```julia
CompetingPoisson(rates; events)

```

与えられた `rates` を持つ競合ポアソン点過程からの最初の到着。

`rand` は `NamedTuple{(:duration,:event)}` を返し、ここで `duration` は最初のイベントまでの期間であり、`event` は `events` から引かれます。

さまざまなプロパティがサポートされています。詳細は [`propertynames`](@ref) を参照してください。

# 注意

`duration` の分布は `Exponential(1/sum(rates))` であるため、このプロセスは競合指数分布とも考えることができます。
