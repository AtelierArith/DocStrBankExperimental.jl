```
FPlane([FT=Float64;] f=nothing, rotation_rate=Ω_Earth, latitude=nothing)
```

定常回転のためのパラメータオブジェクトを返します。角周波数 `f/2` で回転し、したがって背景渦度 `f` を持ち、垂直軸の周りに回転します。`f` が指定されていない場合、`rotation_rate` と `latitude`（度単位）に基づいて `f = 2 * rotation_rate * sind(latitude)` の関係に従って計算されます。

デフォルトでは、`rotation_rate` は地球のものと仮定されます。

また、惑星の回転の局所的な効果を平面座標系で近似する「f-plane」から名付けられた `FPlane` とも呼ばれます。
