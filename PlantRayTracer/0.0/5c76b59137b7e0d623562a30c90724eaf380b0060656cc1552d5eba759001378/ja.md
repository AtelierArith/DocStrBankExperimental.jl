```
TwoSidedSensor(nw::Int)
```

`nw` 波長のための電力を保存するセンサー材料オブジェクトを作成します。両面センサー材料は、方向や照度を変更することなく光線を通過させます。また、光線の反復回数の合計にはカウントされません。蓄積された電力は、センサーの前面と背面に当たる光線ごとに別々に保存されます。

## 例

```jldoctest
julia> s = TwoSidedSensor(1);

julia> s = TwoSidedSensor(3);
```
