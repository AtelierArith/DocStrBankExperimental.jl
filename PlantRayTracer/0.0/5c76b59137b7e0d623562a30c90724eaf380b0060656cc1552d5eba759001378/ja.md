```
TwoSidedSensor(nw::Int)
```

`nw` 波長のための電力を保存するセンサー材料オブジェクトを作成します。両面センサー材料は、光線が方向や照度を変えることなく通過することを許可します。また、光線の反復回数の合計にはカウントされません。蓄積された電力は、センサーの前面と背面に当たる光線のために別々に保存されます。

## 例

```jldoctest
julia> s = TwoSidedSensor(1);

julia> s = TwoSidedSensor(3);
```
