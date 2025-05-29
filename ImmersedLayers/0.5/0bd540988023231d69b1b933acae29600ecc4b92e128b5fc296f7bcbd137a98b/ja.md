```
surface_curl!(w::Nodes{Dual},f::ScalarData,cache::BasicILMCache)
surface_curl!(w::Nodes{Dual},f::ScalarData,sys::ILMSystem)
```

操作 $w = C_s^T f = C^T R_f \mathbf{n}\circ f$ は、スカラー表面データ `f`（スカラー電位のジャンプのようなもの）をグリッドデータ `w`（渦度のようなもの）にマッピングします。これは $C_s$ の随伴であり、引数が入れ替えられた `surface_curl!` でも与えられます。微分操作は、`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、1またはグリッドセルサイズで割られることに注意してください。
