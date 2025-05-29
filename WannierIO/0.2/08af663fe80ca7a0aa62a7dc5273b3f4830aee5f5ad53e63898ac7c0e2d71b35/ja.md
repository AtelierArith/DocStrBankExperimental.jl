```
read_nnkp(filename)
read_nnkp(filename, ::Wannier90Text)
read_nnkp(filename, ::Wannier90Toml)
```

wannier90 `nnkp` ファイルを読み込みます。

# 戻り値

  * `lattice`: 各列は格子ベクトル
  * `recip_lattice`: 各列は逆格子ベクトル
  * `kpoints`: 長さ-`n_kpts` のベクトル、各要素は `Vec3` で、分数座標
  * `projections`: 長さ-`n_projs` の `HydrogenOrbital` ベクトル
  * `auto_projections`: オプション、初期投影のためのWannier関数の数 `n_wann`
  * `kpb_k`: 長さ-`n_kpts` のベクトル、各要素は長さ-`n_bvecs` の整数ベクトルで、k点のインデックス
  * `kpb_G`: 長さ-`n_kpts` のベクトル、各要素は長さ-`n_bvecs` のベクトルで、各要素は `Vec3` で、`recip_lattice` に対する分数の平行移動

Wannier90 `nnkp` ファイルはプレーンテキスト形式で、2番目のバージョンはWannier90形式の `nnkp` ファイルを読み込みます。3番目のバージョンはこのパッケージによって定義されたTOML形式の `nnkp` ファイルを読み込みます。1番目のバージョンは形式を自動検出して解析します。
