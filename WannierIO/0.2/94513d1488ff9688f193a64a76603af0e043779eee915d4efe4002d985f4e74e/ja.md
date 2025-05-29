```
write_nnkp(filename; toml=false, kwargs...)
write_nnkp(filename, ::Wannier90Text; kwargs...)
write_nnkp(filename, ::Wannier90Toml; kwargs...)
```

DFT コードで使用できる `nnkp` ファイルを作成します。例：QE `pw2wannier90`。

# キーワード引数

  * `toml`: TOML ファイルに書き込む。そうでなければ、Wannier90 テキストファイル形式に書き込む
  * `recip_lattice`: 各列は逆格子ベクトル
  * `kpoints`: 長さ-`n_kpts` の `Vec3` ベクトル、分数座標で
  * `kpb_k`: 長さ-`n_kpts` のベクトル、各要素は長さ-`n_bvecs` の整数ベクトルで、k点のインデックス
  * `kpb_G`: 長さ-`n_kpts` のベクトル、各要素は長さ-`n_bvecs` のベクトルで、各要素は `recip_lattice` に対する分数の翻訳ベクトルの `Vec3`
  * `projections`: オプション、長さ-`n_projs` の `HydrogenOrbital` ベクトル
  * `auto_projections`: オプション、自動初期プロジェクションのための Wannier 関数の数 `n_wann`。指定された場合、`auto_projections` ブロックを書き込む
  * `exclude_bands`: 指定された場合、`exclude_bands` ブロックに指定されたバンドインデックスを書き込む
  * `header`: ファイルの最初の行
