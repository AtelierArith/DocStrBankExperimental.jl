```
Path(characteristic_sections::DataFrame)
```

Pathは計算コンテキストのためのデータ構造です。関数Path()は列車の走行経路を作成します。オプション引数:     * points*of*interest::DataFrame # 興味のあるポイント

```
Path(characteristic_sections::DataFrame, points_of_interest::DataFrame)
```

キーワード引数:     * name::String     * id::String     * uuid::UUID

characteristic*sections DataFrameには以下の列が必要です:     * :position,     * :speed,     * :resistance points*of_interest (poi) DataFrameには以下の列が必要です:     * :position,     * :label,     * :measure

# 例

```
julia> my_path = Path(characteristic_sections) # DataFrameから経路を生成します。
Path(variables)
```
