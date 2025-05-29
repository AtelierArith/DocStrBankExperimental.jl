```
get_chordal_extension(sp_pattern::SparseMatrixCSC; perm="amd", verbose=false)
```

返す `p, ip, L` は、`L` が無向グラフ `sp_pattern` の和音拡張を表す下三角行列であり、フィル削減置換 `p`（逆置換 `ip` とともに）を適用した後のものです。

perm のオプションには以下が含まれます： 	- `"nothing"`（置換なし） 	- `amd`（近似最小次数） 	- `metis`（[METIS](http://glaros.dtc.umn.edu/gkhome/metis/metis/overview) を使用） 	- `cuthill-mckee`（Cuthill-McKee 帯域幅削減アルゴリズム）
