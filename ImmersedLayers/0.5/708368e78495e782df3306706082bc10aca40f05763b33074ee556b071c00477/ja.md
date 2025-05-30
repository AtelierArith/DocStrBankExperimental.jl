```
surface_curl_cross!(w::Nodes{Dual},f::ScalarData,cache::BasicILMCache)
surface_curl_cross!(w::Nodes{Dual},f::ScalarData,sys::ILMSystem)
```

操作 $w = \hat{C}_s^T f = C^T R_f \mathbf{n}\times f \mathbf{e}_z$ は、スカラー表面データ `f`（流れ関数のジャンプのようなもので、面外単位ベクトル $\mathbf{e}_z$ で乗算される）をグリッドデータ `w`（渦度のようなもの）にマッピングします。これは $\hat{C}_s$ の随伴であり、引数が入れ替わった `surface_curl_cross!` によっても与えられます。`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、微分操作は1またはグリッドセルサイズで割られることに注意してください。
