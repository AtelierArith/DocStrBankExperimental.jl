```
surface_curl!(vn::ScalarData,s::Nodes{Dual},cache::BasicILMCache)
surface_curl!(vn::ScalarData,s::Nodes{Dual},sys::ILMSystem)
```

操作 $v_n = C_s s = \mathbf{n} \cdot R_f^T C s$ は、グリッドデータ `s`（流れ関数のような）をスカラー表面データ `vn`（速度の法線成分のような）にマッピングします。これは $C_s^T$ の随伴であり、引数が入れ替わった `surface_curl!` でもあります。`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、微分操作は1またはグリッドセルサイズで割られることに注意してください。
