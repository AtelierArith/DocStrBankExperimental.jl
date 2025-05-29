```
cbct_back(proj, rg, ig)
```

コーンビーム逆投影器 for feldkamp.jl

# 入力

  * `proj (ns,nt,na)` コーンビーム投影ビュー
  * `rg::CtGeom`
  * `ig::ImageGeom`

# 出力

  * `img (nx,ny,nz)` 逆投影結果
