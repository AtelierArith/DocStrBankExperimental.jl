```
batchseq(seqs, val = 0)
```

`N` 個のシーケンスのリストを受け取り、それらを単一のシーケンスに変換します。各アイテムは `N` のバッチです。短いシーケンスは `val` でパディングされます。

# 例

```jldoctest
julia> batchseq([[1, 2, 3], [4, 5]], 0)
3-element Vector{Vector{Int64}}:
 [1, 4]
 [2, 5]
 [3, 0]
```
