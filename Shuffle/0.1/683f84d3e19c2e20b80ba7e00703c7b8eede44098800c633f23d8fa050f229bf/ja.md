```
シャッフル
```

決定論的およびランダムなシャッフルアルゴリズムのいくつかをサポートします。関数 [`shuffle`](@ref)、[`shuffle!`](@ref)、[`nshuffle`](@ref)、および [`nshuffle!`](@ref) を提供し、次のシャッフルアルゴリズムを含みます：

  * [ファーロ（またはウィーブ）シャッフル](https://luapulu.github.io/Shuffle.jl/stable/reference/#Shuffle.Faro),
  * [カット](https://luapulu.github.io/Shuffle.jl/stable/reference/#Shuffle.Cut),
  * [ランダムシャッフル](https://luapulu.github.io/Shuffle.jl/stable/reference/#Shuffle.RandomShuffle)   （[`Random.shuffle`](https://docs.julialang.org/en/v1/stdlib/Random/#Random.shuffle)を使用）および
  * [ギルバート-シャノン-リードモデル](https://luapulu.github.io/Shuffle.jl/stable/reference/#Shuffle.GilbertShannonReeds).
