```
initnoise(seed::Int)
initnoise()
```

Initialize the noise generation code.

```julia-repl
julia> initnoise(); noise(1)
0.7453148982810598

julia> initnoise(); noise(1)
0.7027617067916981
```

If you provide an integer seed, it will be used to seed `Random.seed!()` when the noise code is initialized:

```julia-repl
julia> initnoise(41); noise(1) # yesterday
0.7134000046640385

julia> initnoise(41); noise(1) # today
0.7134000046640385
```

If you need to control which type of random number generator is used, you can provide your own and it will be used instead of the default Julia implementation.

```julia-repl
julia> rng = MersenneTwister(1234) # any AbstractRNG
julia> initnoise(rng)
```
