```
fit!(stat1::OnlineStat, stat2::OnlineStat)
```

`merge!`のエイリアス。`stat2`を`stat1`にマージします。

`fit!`を使用したOnlineStatsの集約に便利です。

# 例

```julia-repl
julia> v = [reduce(fit!, [1, 2, 3], init=Mean()) for _ in 1:3]
3-element Vector{Mean{Float64, EqualWeight}}:
Mean: n=3 | value=2.0
Mean: n=3 | value=2.0
Mean: n=3 | value=2.0

julia> reduce(fit!, v, init=Mean())
Mean: n=9 | value=2.0
```
