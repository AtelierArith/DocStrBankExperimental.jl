```
surface_curl!(v::VectorData,s::Nodes{Dual},cache::BasicILMCache)
surface_curl!(v::VectorData,s::Nodes{Dual},sys::ILMSystem)
```

操作 $\mathbf{v} = C_s s = R_f^T C s$ は、グリッドデータ `s`（流れ関数のような）をベクトル表面データ `v`（速度のような）にマッピングします。これは $C_s^T$ の随伴であり、引数が入れ替わった `surface_curl!` でも与えられます。`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、微分操作は1またはグリッドセルサイズで割られることに注意してください。
