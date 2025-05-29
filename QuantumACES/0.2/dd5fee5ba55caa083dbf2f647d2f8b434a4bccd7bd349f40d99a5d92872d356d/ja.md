```
get_pad_transform(gate_data::GateData; probabilities::Bool = false)
```

ゲートデータ `gate_data` を使用して、ゲートの固有値をパディングする変換行列、または `probabilities` が `true` の場合はゲートエラー確率を、恒常的に [`get_pad_mask`](@ref) によって与えられる値まで、アイデンティティの固有値またはエラー確率でパディングします。
