```
PinchData{T}
```

固定温度間隔のデータで、`T_SH_hot` と `T_SH_cold` で動作する余剰エネルギー源からの利用可能エネルギーを計算するために使用され、`T_DH_hot` と `T_DH_cold` で動作する地域暖房ネットワークとの間の余剰源との `ΔT_min` があります。

この構造体は内部で使用され、`AbstractHeatExchanger` の出入りする `ResourceHeat` の供給温度と戻り温度から計算されます。
