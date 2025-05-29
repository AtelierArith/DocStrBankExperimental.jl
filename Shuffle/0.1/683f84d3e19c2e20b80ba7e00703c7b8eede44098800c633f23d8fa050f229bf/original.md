```
Shuffle
```

Support for a number of deterministic and random shuffling algorithms. Provides functions [`shuffle`](@ref), [`shuffle!`](@ref), [`nshuffle`](@ref) and [`nshuffle!`](@ref) as well as the following shuffling algorithms:

  * [faro (or weave) shuffle](https://luapulu.github.io/Shuffle.jl/stable/reference/#Shuffle.Faro),
  * a [cut](https://luapulu.github.io/Shuffle.jl/stable/reference/#Shuffle.Cut),
  * [random shuffle](https://luapulu.github.io/Shuffle.jl/stable/reference/#Shuffle.RandomShuffle)   (uses [`Random.shuffle`](https://docs.julialang.org/en/v1/stdlib/Random/#Random.shuffle)) and
  * [Gilbert-Shannon-Reeds model](https://luapulu.github.io/Shuffle.jl/stable/reference/#Shuffle.GilbertShannonReeds).
