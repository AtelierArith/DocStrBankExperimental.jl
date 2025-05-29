```
surface_curl!(w::Nodes{Dual},v::VectorData,cache::BasicILMCache)
surface_curl!(w::Nodes{Dual},v::VectorData,sys::ILMSystem)
```

操作 $w = C_s^T \mathbf{v} = C^T R_f \mathbf{v}$ は、ベクトル表面データ `v`（速度のような）をグリッドデータ `w`（渦度のような）にマッピングします。これは $C_s$ の随伴であり、引数が入れ替えられた `surface_curl!` でも与えられます。`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、微分操作はそれぞれ 1 またはグリッドセルサイズで割られることに注意してください。
