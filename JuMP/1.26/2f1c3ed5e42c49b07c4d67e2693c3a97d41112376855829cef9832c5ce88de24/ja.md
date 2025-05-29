```
result_count(model::GenericModel)
```

[`optimize!`](@ref) の呼び出し後にクエリ可能な結果の数を返します。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> result_count(model)
0
```
