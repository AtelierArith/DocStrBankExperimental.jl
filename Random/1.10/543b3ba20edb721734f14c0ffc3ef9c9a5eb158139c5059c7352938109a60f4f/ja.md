```
MersenneTwister(seed)
MersenneTwister()
```

`MersenneTwister` RNGオブジェクトを作成します。異なるRNGオブジェクトはそれぞれ独自のシードを持つことができ、異なる乱数のストリームを生成するのに役立ちます。`seed`は非負整数または`UInt32`整数のベクターである場合があります。シードが提供されない場合は、ランダムに生成されたものが作成されます（システムからのエントロピーを使用）。既存の`MersenneTwister`オブジェクトの再シードについては、[`seed!`](@ref)関数を参照してください。

# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.5908446386657102
 0.7667970365022592

julia> rng = MersenneTwister(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.5908446386657102
 0.7667970365022592

julia> x1 == x2
true
```
