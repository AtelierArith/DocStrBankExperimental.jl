```
Rate(rate[,frequency=1])
Rate(rate,frequency::Frequency)
```

Rateは、利率`rate`とその複利`frequency`をカプセル化する型です。

定期的な利率は、`Rate(rate,frequency)`または`Rate(rate,Periodic(frequency))`を介して構築できます。第二引数が指定されていない場合、`Rate(rate)`は`Rate(rate,Periodic(1))`と同等です。

連続的な利率は、`Rate(rate, Inf)`または`Rate(rate,Continuous())`を介して構築できます。

# 例

```julia-repl
julia> Rate(0.01,Continuous())
Rate(0.01, Continuous())

julia> Continuous(0.01)
Rate(0.01, Continuous())

julia> Continuous()(0.01)
Rate(0.01, Continuous())

julia> Rate(0.01,Periodic(2))
Rate(0.01, Periodic(2))

julia> Periodic(0.01,2)
Rate(0.01, Periodic(2))

julia> Periodic(2)(0.01)
Rate(0.01, Periodic(2))

julia> Rate(0.01)
Rate(0.01, Periodic(1))

julia> Rate(0.01,2)
Rate(0.01, Periodic(2))

julia> Rate(0.01,Periodic(4))
Rate(0.01, Periodic(4))

julia> Rate(0.01,Inf)
Rate(0.01, Continuous())

```
