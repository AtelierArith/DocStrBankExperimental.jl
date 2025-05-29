```
set_value(p::NonlinearParameter, v::Number)
```

非線形パラメータ `p` に値 `v` を格納します。

# 例

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameter(model, p == 0)
set_value(p, 5)
value(p)

# 出力
5.0
```
