```
isempty(model::GenericModel)
```

モデルが空であるかどうかを確認します。つまり、MOIバックエンドが空であるか、最適化属性を除いてモデルが作成時と同じ状態であるかどうかを確認します。

## 例

```jldoctest
julia> model = Model();

julia> isempty(model)
true

julia> @variable(model, x[1:2]);

julia> isempty(model)
false
```
