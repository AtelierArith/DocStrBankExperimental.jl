```
lrsnash(g)
```

整数または有理数の報酬を持つ2人用通常形ゲームのすべての極端な混合行動ナッシュ均衡を正確な算術で計算します。この関数は、"lexicographic reverse search" 頂点列挙アルゴリズムに基づく `lrslib` のナッシュ均衡計算ルーチンを呼び出します（そのJuliaラッパー `LRSLib.jl` を通じて）。

# 引数

  * `g::NormalFormGame{2,<:RatOrInt}`: 整数または有理数の報酬を持つ2人用NormalFormGameインスタンス。

# 戻り値

  * `::Vector{NTuple{2,Vector{Rational{BigInt}}}}`: 混合行動ナッシュ均衡のベクトル。

# 例

退化ゲームの例：

```julia
julia> player1 = Player([3 3; 2 5; 0 6]);

julia> player2 = Player([3 2 3; 3 6 1]);

julia> g = NormalFormGame(player1, player2);

julia> println(g)
3×2 NormalFormGame{2, Int64}:
 [3, 3]  [3, 3]
 [2, 2]  [5, 6]
 [0, 3]  [6, 1]

julia> lrsnash(g)
3-element Vector{Tuple{Vector{Rational{BigInt}}, Vector{Rational{BigInt}}}}:
 ([1//1, 0//1, 0//1], [1//1, 0//1])
 ([1//1, 0//1, 0//1], [2//3, 1//3])
 ([0//1, 1//3, 2//3], [1//3, 2//3])
```

この退化ゲームのナッシュ均衡の集合は、孤立した均衡（3番目の出力）と、最初の2つの出力によって与えられる極端な点を持つ非単一均衡成分から構成されています。

# 参考文献

  * D. Avis, G. Rosenberg, R. Savani, and B. von Stengel, "Enumeration of Nash Equilibria for Two-Player Games," Economic Theory (2010), 9-37.
