```
shuffle!([rng=GLOBAL_RNG,] df::AbstractDataFrame)
```

`df`の行をランダムに並べ替えます。オプションの`rng`引数は乱数生成器を指定します。

`shuffle!`は、渡されたデータフレームのいくつかの列が同一であっても（`===`でチェックされる）正しい結果を生成します。そうでなければ、2つの列がメモリの一部を共有しているが同一でない場合（例えば、同じ親ベクトルの異なるビューである場合）、`shuffle!`の結果が不正確になる可能性があります。

メタデータ：この関数はテーブルレベルおよび列レベルの`:note`スタイルのメタデータを保持します。

他のスタイルのメタデータは削除されます（`df`が`SubDataFrame`の場合、親データフレームから）。

# 例

```jldoctest
julia> using Random

julia> rng = MersenneTwister(1234);

julia> shuffle!(rng, DataFrame(a=1:5, b=1:5))
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
