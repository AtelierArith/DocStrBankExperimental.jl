```
prefix(model::Model, x::VarName)
prefix(model::Model, x::Val{sym})
prefix(model::Model, x::Any)
```

`model`を返しますが、すべてのランダム変数には`x`が接頭辞として付けられます。ここで、`x`は次のいずれかです：

  * `VarName`（例：`@varname(a)`）、
  * `Val{sym}`（例：`Val(:a)`）、または
  * その他の型の場合、`x`はSymbolに変換され、その後`VarName`に変換されます。これは実行時のオーバーヘッドを引き起こすため、絶対に必要な場合を除いて推奨されません。

# 例

```jldoctest
julia> using DynamicPPL: prefix

julia> @model demo() = x ~ Dirac(1)
demo (generic function with 2 methods)

julia> rand(prefix(demo(), @varname(my_prefix)))
(var"my_prefix.x" = 1,)

julia> rand(prefix(demo(), Val(:my_prefix)))
(var"my_prefix.x" = 1,)
```
