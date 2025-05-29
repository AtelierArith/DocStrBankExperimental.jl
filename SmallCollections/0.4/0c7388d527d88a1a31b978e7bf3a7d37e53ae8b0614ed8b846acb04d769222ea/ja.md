```
prepend(v::V, ws...) where V <: AbstractCapacityVector -> V
```

コレクション `ws` のすべての要素を `v` の先頭に追加し、新しいベクターを返します。結果として得られる `AbstractCapacityVector` は `v` と同じ容量を持つことに注意してください。

また、`Base.prepend!` も参照してください。
