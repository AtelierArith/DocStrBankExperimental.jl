```
deleteat(v::V, i::Integer) where V <: AbstractCapacityVector -> V
```

位置 `i` の要素を削除することによって `v` から得られる `AbstractCapacityVector` を返します。`i` は `1` から `length(v)` の間でなければなりません。

また、`Base.deleteat!`、`BangBang.deleteat!!` も参照してください。
