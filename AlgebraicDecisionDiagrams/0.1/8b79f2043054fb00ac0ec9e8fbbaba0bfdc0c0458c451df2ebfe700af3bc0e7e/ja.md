```
restrict(α::DecisionDiagram, var::Int, value::Bool=true)
```

変数 var=value で制約された関数 α の標準形を返します。

# 例

```julia
x, y = variable(1), variable(2)
f = (one(x)-x)*(one(y)-1) + x*y
g = Terminal(4)*(one(x)-x) + Terminal(2)*x
h = f + g
r1 = restrict(h,1,false)
r2 = h | (2 => true) # restrict(h,2,true) の省略形
r3 = h | (y => true) # 上と同じ
```
