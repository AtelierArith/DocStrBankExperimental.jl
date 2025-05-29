```
shuffle([rng=GLOBAL_RNG,] df::AbstractDataFrame)
```

`df`の行をランダムに並べ替えたコピーを返します。オプションの`rng`引数は乱数生成器を指定します。

メタデータ: この関数はテーブルレベルおよびカラムレベルの`:note`スタイルのメタデータを保持します。

# 例

```jldoctest
julia> using Random

julia> rng = MersenneTwister(1234);

julia> shuffle(rng, DataFrame(a=1:5, b=1:5))
5×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     2      2
   2 │     1      1
   3 │     4      4
   4 │     3      3
   5 │     5      5
```
