```
all_variables(model::Model)::Vector{VariableRef}
```

モデル内のすべての変数のリストを返します。変数は作成時間順に並べられています。

# 例

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
@variable(model, y)
all_variables(model)

# 出力

2-element Array{VariableRef,1}:
 x
 y
```
