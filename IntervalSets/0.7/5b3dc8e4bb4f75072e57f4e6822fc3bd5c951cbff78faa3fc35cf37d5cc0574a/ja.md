```
searchsorted_interval(a, i::Interval; [rev=false])
```

`a` の中で区間 `i` に含まれるインデックスの範囲を返します（バイナリサーチを使用）。`a` はすでにソートされていると仮定します。`a` が `i` の値を含まない場合は、挿入ポイントに位置する空の範囲を返します。

# 例

```jldoctest
julia> searchsorted_interval([1,2,3,5], 2..4)
2:3

julia> searchsorted_interval([1,2,3,5], 4..1)
4:3

julia> searchsorted_interval(Float64[], 1..3)
1:0
```
