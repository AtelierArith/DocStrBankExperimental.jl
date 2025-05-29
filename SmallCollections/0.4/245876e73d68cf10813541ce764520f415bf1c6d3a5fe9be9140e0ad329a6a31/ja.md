```
push(v::V, xs...) where V <: AbstractCapacityVector -> V
```

引数 `xs` を追加することによって `v` から得られる `AbstractCapacityVector` を返します。

関連情報として `Base.push!`、`BangBang.push!!` を参照してください。
