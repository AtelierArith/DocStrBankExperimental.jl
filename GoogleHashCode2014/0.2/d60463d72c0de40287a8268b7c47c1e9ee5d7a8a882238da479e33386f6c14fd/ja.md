```
解決策
```

[`City`](@ref)を通る旅程のリストを、各車両ごとに保存します。

単純な`Solution`は、関数[`random_walk`](@ref)を使って計算できます。

# フィールド

  * `itineraries::Vector{Vector{Int}}`: 各旅程は交差点インデックスのベクターです

# 例

```jldoctest
julia> using GoogleHashCode2014, Random

julia> city = read_city();

julia> rng = Random.MersenneTwister(0);

julia> solution = random_walk(rng, city)
Solution with 8 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366, 3707]

julia> length(solution.itineraries[2])  # 車両番号2が訪れた交差点の数
3277

julia> solution.itineraries[2][1:10]  # 車両番号2が訪れた最初の10個の交差点インデックス
10-element Vector{Int64}:
  4517
  1033
  3656
  7681
   398
  4680
 10361
 10089
 10361
 10089
```
