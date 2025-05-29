```
append(v::V, ws...) where V <: AbstractCapacityVector -> V
```

コレクション `ws` のすべての要素を `v` に追加し、新しいベクターを返します。結果として得られる `AbstractCapacityVector` は `v` と同じ容量を持つことに注意してください。

また、`Base.append!`、`BangBang.append!!` も参照してください。
