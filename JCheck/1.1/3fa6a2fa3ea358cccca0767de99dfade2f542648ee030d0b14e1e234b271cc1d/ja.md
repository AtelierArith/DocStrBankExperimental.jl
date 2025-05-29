```
@getcases ft, desc...
```

記述 `desc` を持つ述語と、それが失敗した評価を取得します。

# 注記

与えられた記述に最も近い（レーベンシュタイン距離の意味で）述語が返されます。正確な記述を渡す必要はありません。

# 例

```jldoctest
julia> ft = JCheck.load("JCheck_test.jchk")
2 つの失敗した述語:
積の交換法則
奇数である

julia> pred, valuations = @getcases ft iod
NamedTuple{(:predicate, :valuations), Tuple{Function, Vector{Tuple}}}((Serialization.__deserialized_types__.var"#3#4"(), Tuple[(0,), (-9223372036854775808,), (6444904272543528628,)]))

julia> map(x -> pred(x...), valuations)
3-element Vector{Bool}:
 0
 0
 0
```
