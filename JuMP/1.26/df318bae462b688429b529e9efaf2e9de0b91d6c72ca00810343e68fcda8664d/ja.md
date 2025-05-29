```
owner_model(s::AbstractJuMPScalar)
```

スカラー `s` を所有するモデルを返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> owner_model(x) === model
true
```
