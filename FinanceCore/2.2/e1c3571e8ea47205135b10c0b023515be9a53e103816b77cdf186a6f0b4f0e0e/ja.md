```
Periodic(rate,frequency)
```

Rate(rate,Periodic(frequency))の便利なコンストラクタです。

# 例

半年ごとの債券相当利回りを作成する:

```julia-repl
julia> Periodic(0.01,2)
Rate(0.01, Periodic(2))
```

関連項目: [`Continuous`](@ref)
