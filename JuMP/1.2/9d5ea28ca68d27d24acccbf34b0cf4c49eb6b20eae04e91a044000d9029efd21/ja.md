```
value(p::NonlinearParameter)
```

非線形パラメータ `p` に格納されている現在の値を返します。

# 例

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameter(model, p == 10)
value(p)

# 出力
10.0
```
