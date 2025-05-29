```
random_nearby_position(pos, model::ABM, r=1, f = nothing, alloc = false; kwargs...) → position
```

指定された位置の近くのランダムな位置を返します。近くの位置が許可されていない場合は `nothing` を返します。

引数 `r` の値と可能なキーワードは [`nearby_positions`](@ref) と同様に動作します。

フィルタ関数 `f(pos)` を渡すことで、関数が `true` を返す位置のみにサンプリングを制限できます。フィルタリング条件が高コストの場合は、引数 `alloc` を使用できます。この場合、割り当て版の方がパフォーマンスが向上する可能性があります。`f` を満たす近くの位置がない場合は `nothing` が返されます。
