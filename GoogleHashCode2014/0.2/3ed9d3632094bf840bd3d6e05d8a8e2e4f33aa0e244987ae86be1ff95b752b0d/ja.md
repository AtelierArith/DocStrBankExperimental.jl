```
ジャンクション
```

[`City`](@ref)からジャンクションを保存します。

!!! tip
    ジャンクションは通常、都市のジャンクションリスト内の整数インデックスで参照されます。ジャンクションオブジェクト自体は主に地理的視覚化に役立ちます。


# フィールド

  * `latitude::Float64`: 緯度（小数度）
  * `longitude::Float64`: 経度（小数度）

# 例

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city();

julia> junction = city.junctions[10]  # ジャンクションインデックス10のジャンクションオブジェクトを取得
Junction at coordinates (48.872250900000004, 2.3124588)

julia> junction.latitude
48.872250900000004
```
