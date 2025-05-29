```
set_value(p::NonlinearParameter, v::Number)
```

非線形パラメータ `p` に値 `v` を格納します。

!!! compat
    この関数はレガシー非線形インターフェースの一部です。[非線形モデリング](@ref)で文書化されている新しい非線形インターフェースの使用を検討してください。


## 例

```jldoctest
julia> model = Model();

julia> @NLparameter(model, p == 0)
p == 0.0

julia> set_value(p, 5)
5

julia> value(p)
5.0
```
