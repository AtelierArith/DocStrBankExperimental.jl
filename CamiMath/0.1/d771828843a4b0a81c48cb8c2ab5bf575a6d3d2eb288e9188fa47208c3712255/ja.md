```
convertToBig(x::T) where T
```

64ビットベースの型からBigIntベースの型への変換:

  * Int => BigInt,
  * Vector{Int}                      => Vector{BigInt},
  * Vector{Vector{Int}}              => Vector{Vector{BigInt}},
  * Rational{Int}                    => Rational{BigInt},
  * Vector{Rational{Int}}            => Vector{Rational{BigInt}},
  * Vector{Vector{Rational{Int}}}    => Vector{Vector{Rational{BigInt}}},
  * Float64                          => BigFloat,
  * Vector{Float64}                  => Vector{BigFloat},
  * Vector{Vector{Float64}}          => Vector{Vector{BigFloat}},
  * Complex{Float64}                 => Complex{BigFloat},
  * Vector{Complex{Float64}}         => Vector{Complex{BigFloat}},
  * Vector{Vector{Complex{Float64}}} => Vector{Vector{Complex{BigFloat}}}

#### 例:

```
julia> [[1 // 1, 1 // 2], [1 // 1, 1 // 2]]
2-element Vector{Vector{Rational{Int64}}}:
 [1, 1//2]
 [1, 1//2]

julia> convertToBig([[1 // 1, 1 // 2], [1 // 1, 1 // 2]])
2-element Vector{Vector{Rational{BigInt}}}:
 [1, 1//2]
 [1, 1//2]
```
