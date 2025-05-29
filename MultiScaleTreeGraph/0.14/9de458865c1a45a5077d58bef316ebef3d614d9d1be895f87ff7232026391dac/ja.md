```
branching_order!(mtg; ascend = true)
```

mtg内のノードのトポロジカルブランチングオーダーを計算します。

# 引数

  * `mtg`: mtg、*例* `read_mtg()`の出力
  * `ascend`: `true`の場合、基部（アクロペタル）から順序が計算され、`false`の場合、

先端（バシペタル）から計算されます。

# 注意事項

ノードの順序は、バシペタル計算を使用する際に、その子の最大順序から計算されます。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)
branching_order!(mtg)
DataFrame(mtg, :branching_order)
# 7×2 DataFrame
#  Row │ tree                        branching_order
#      │ String                      Int64
# ─────┼───────────────────────────────────────────────
#    1 │ / 1: $                                      1
#    2 │ └─ / 2: Individual                          1
#    3 │    └─ / 3: Axis                             1
#    4 │       └─ / 4: Internode                     1
#    5 │          ├─ + 5: Leaf                       2
#    6 │          └─ < 6: Internode                  1
#    7 │             └─ + 7: Leaf                    2

branching_order!(mtg, ascend = false)
DataFrame(mtg, :branching_order)
# 7×2 DataFrame
#  Row │ tree                        branching_order
#      │ String                      Int64
# ─────┼───────────────────────────────────────────────
#    1 │ / 1: $                                      2
#    2 │ └─ / 2: Individual                          2
#    3 │    └─ / 3: Axis                             2
#    4 │       └─ / 4: Internode                     2
#    5 │          ├─ + 5: Leaf                       1
#    6 │          └─ < 6: Internode                  2
#    7 │             └─ + 7: Leaf                    1
```
