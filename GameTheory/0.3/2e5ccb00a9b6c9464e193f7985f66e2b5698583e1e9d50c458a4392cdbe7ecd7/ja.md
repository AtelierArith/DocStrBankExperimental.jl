```
random_game([rng=GLOBAL_RNG], [S=Float64], nums_actions)
```

N人プレイヤーのノーマルフォームゲームインスタンスをランダムに返します。報酬は`S`によって決定される集合から独立に一様分布から引かれます。`S`は範囲（例えば`0:9`）または`Integer`または`AbstractFloat`のサブタイプです。後者の場合、集合は浮動小数点数の場合は[0, 1)であり、整数の場合は`typemin(S):typemax(S)`です。

# 引数

  * `rng::AbstractRNG=GLOBAL_RNG`: 使用される乱数生成器。
  * `S::Union{Type,AbstractRange}`: 報酬が引かれる値の集合。
  * `nums_actions::NTuple{N,Int}`: 各プレイヤーのアクション数のタプル。

# 戻り値

  * `::NormalFormGame`: 生成されたランダムなN人プレイヤーのノーマルフォームゲーム。

# 例

```julia
julia> using GameTheory, Random

julia> rng = MersenneTwister(12345);

julia> g = random_game(rng, (4, 3));

julia> println(g)
4×3 NormalFormGame{2, Float64}:
 [0.562714, 0.586598]  [0.381128, 0.0501668]  [0.922317, 0.61179]
 [0.849939, 0.620099]  [0.365801, 0.215712]   [0.0404417, 0.569955]
 [0.371605, 0.965631]  [0.835014, 0.364706]   [0.573382, 0.923602]
 [0.283365, 0.754047]  [0.260024, 0.696476]   [0.981364, 0.0311643]

julia> g = random_game(rng, 0:9, (4, 3));

julia> println(g)
4×3 NormalFormGame{2, Int64}:
 [1, 5]  [1, 2]  [6, 2]
 [2, 5]  [0, 2]  [1, 0]
 [0, 5]  [3, 9]  [1, 1]
 [9, 5]  [2, 9]  [0, 6]
```
