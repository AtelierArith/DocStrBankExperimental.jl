```
JuMP.result_count(model::InfiniteModel)
```

`result_count`を拡張して、`optimize!`の呼び出し後にクエリ可能な結果の数を返すようにします。

**例**

```julia-repla
julia> result_count(model)
1
```
