```
element!(model::Model, ID::Int,
    node_i_ID  ::Int,
    node_j_ID  ::Int,
    section_ID ::Int,
    material_ID::Int;
    ω          ::Real = 0,
    releases_i ::Vector{<:Bool} = [false, false, false],
    releases_j ::Vector{<:Bool} = [false, false, false])::Model
```

有限要素モデルに要素を追加します。
