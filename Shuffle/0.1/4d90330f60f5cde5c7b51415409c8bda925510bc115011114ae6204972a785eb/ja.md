```
AbstractRandomShuffle <: AbstractShuffle
```

部分的または完全にランダムなシャッフルアルゴリズムのスーパークラスであり、[`RandomShuffle`](@ref)や[`GilbertShannonReeds`](@ref)などがあります。

# 実装

新しいランダムシャッフルアルゴリズムは、適切に[`shuffle`](@ref)または[`shuffle!`](@ref)のいずれかを実装する必要があります。新しいシャッフルメソッドは、最初の引数として[`Random.AbstractRNG`](https://docs.julialang.org/en/v1/stdlib/Random/#Random.AbstractRNG)を、2番目の引数としてシャッフルされるコレクションを、3番目の引数として新しいシャッフルアルゴリズムタイプのインスタンスを取るべきです。

例えば：

```julia
struct MyShuffle <: AbstractRandomShuffle end

function shuffle!(r::AbstractRNG, c, s::MyShuffle)
    # シャッフルを行い、rを任意の乱数生成関数に渡します

    return c
end
```

参照：[`AbstractShuffle`](@ref)
