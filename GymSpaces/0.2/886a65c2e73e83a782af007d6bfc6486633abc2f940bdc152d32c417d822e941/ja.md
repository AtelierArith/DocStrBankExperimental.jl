```
seed!(dict_obj::DictSpace; kwarg_seeds...)
```

DictSpace内のスペースにシードを設定します。現在、Symbolキーのみを持つDictSpaceのシード設定が許可されています。

# 例

julia> space = DictSpace(Dict(:position => Discrete(5),                               :velocity => Box([0, 0], [1, 5], Float32))) . . .

julia> seed!(space, position=42)

julia> seed!(space, position=2, velocity=4)
