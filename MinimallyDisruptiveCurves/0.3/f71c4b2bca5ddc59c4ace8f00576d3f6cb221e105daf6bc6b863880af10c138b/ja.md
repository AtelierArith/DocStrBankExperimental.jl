```
CurveDistance(timepoints::AbstractRange)
CurveDistance(timepoints::Vector{<:AbstractFloat})
```

各 timepoints::Vector{<:AbstractFloat} に達したときの曲線距離を @info REPL 出力として表示します。

例 c = CurveDistance(0.1:0.1:2.1)

c はその後、Verbose() の引数として使用でき、次に evolve へのキーワード引数として渡されます。
