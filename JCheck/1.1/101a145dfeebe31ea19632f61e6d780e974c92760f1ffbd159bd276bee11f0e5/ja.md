```
load(io)
```

[`@quickcheck`](@ref) 実行によってシリアライズされた失敗したテストケースのコレクションをロードします。引数 `io` は `IO`、`AbstractString` または `AbstractPath` の型であることができます。

# 例

```jldoctest
julia> ft = JCheck.load("JCheck_test.jchk")
2 つの失敗した述語:
積の可換性
奇数であること
```
