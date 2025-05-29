```
pushfirst((v::V, xs...) where V <: AbstractCapacityVector -> V
```

引数 `xs` を先頭に追加することによって `v` から得られる `AbstractCapacityVector` を返します。

また、`Base.pushfirst!`、`BangBang.pushfirst!!` も参照してください。
