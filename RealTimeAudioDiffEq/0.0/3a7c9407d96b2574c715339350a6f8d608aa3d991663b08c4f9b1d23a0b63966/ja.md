```
DESource(f, g, u0::Vector{Float64}, p::Vector{Float64};
	alg = SOSRA(), channel_map::Vector{Int} = [1, 1])::DESource
```

ドリフト関数とノイズ関数から確率的DESourceを作成します。
