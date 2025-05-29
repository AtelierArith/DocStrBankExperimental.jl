```
surface_curl_cross!(γ::ScalarData,s::Nodes{Dual},cache::BasicILMCache)
surface_curl_cross!(γ::ScalarData,s::Nodes{Dual},sys::ILMSystem)
```

操作 $\gamma = \hat{C}_s s = \mathbf{e}_z\cdot (\mathbf{n} \times R_f^T C s)$ は、グリッドデータ `s`（流れ関数のような）をスカラー表面データ `γ`（表面の渦度のような）にマッピングします。これは $\hat{C}_s^T$ の随伴であり、引数が入れ替わった `surface_curl_cross!` でも与えられます。`sys` が `IndexScaling` または `GridScaling` で指定されているかどうかに応じて、微分操作は1またはグリッドセルサイズで割られることに注意してください。
