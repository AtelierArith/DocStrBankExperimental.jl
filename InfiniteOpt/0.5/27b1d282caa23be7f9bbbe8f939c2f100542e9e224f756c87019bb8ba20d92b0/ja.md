```
JuMP.set_silent(model::InfiniteModel)
```

無限モデルに対して `JuMP.set_silent` を拡張し、冗長性を制御する他の属性よりも優先され、ソルバーが出力を生成しないことを要求します。

**例**

```julia-repl
julia> set_silent(model)
true
```
