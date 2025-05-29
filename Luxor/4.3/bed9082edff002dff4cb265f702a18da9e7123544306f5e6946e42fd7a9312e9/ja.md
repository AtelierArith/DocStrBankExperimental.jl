```
initnoise(seed::Int)
initnoise()
```

ノイズ生成コードを初期化します。

```julia-repl
julia> initnoise(); noise(1)
0.7453148982810598

julia> initnoise(); noise(1)
0.7027617067916981
```

整数のシードを提供すると、ノイズコードが初期化されるときに `Random.seed!()` のシードとして使用されます：

```julia-repl
julia> initnoise(41); noise(1) # 昨日
0.7134000046640385

julia> initnoise(41); noise(1) # 今日
0.7134000046640385
```

使用する乱数生成器のタイプを制御する必要がある場合は、自分のものを提供すると、デフォルトのJulia実装の代わりに使用されます。

```julia-repl
julia> rng = MersenneTwister(1234) # 任意のAbstractRNG
julia> initnoise(rng)
```
