```
velocity_spherical_to_cartesian!(Data::GeoData, Velocity::Tuple)
```

球面速度 `[Veast, Vnorth, Vup]` を直交座標系にインプレースで変換します（paraviewで使用するため）。

注意：ベクトルの大きさは同じですが、個々の `[Veast, Vnorth, Vup]` コンポーネントは正しく保持されません（paraviewでは異なる `[x,y,z]` 座標系が使用されるため）。したがって、Paraviewでそれを正しく表示または色付けしたい場合は、これらの大きさを別のフィールドとして保存する必要があります。
