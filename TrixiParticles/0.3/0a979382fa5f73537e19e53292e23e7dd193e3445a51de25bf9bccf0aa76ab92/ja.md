```
ColorfieldSurfaceNormal(; boundary_contact_threshold=0.1, interface_threshold=0.01,
                          ideal_density_threshold=0.0)
```

色フィールドに基づくインターフェース法線の計算。

# キーワード引数

  * `boundary_contact_threshold=0.1`: この閾値に達すると、流体は境界に接触していると見なされます。
  * `interface_threshold=0.01`:       無効と見なされる法線を削除するための閾値。
  * `ideal_density_threshold=0.0`:    この閾値を超える粒子は内部にあると見なします。これは `ideal_neighbor_count` に対して相対的です。
