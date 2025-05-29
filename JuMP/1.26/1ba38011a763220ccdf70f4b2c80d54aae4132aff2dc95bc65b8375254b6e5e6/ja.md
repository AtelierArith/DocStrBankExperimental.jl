```
value(p::NonlinearParameter)
```

非線形パラメータ `p` に格納されている現在の値を返します。

## 例

```jldoctest
julia> model = Model();

julia> @NLparameter(model, p == 10)
p == 10.0

julia> value(p)
10.0
```
