```
write_mmn(filename; M, kpb_k, kpb_G; header=default_header(), binary=false)
write_mmn(filename; M, kpb_k, kpb_G, ::FortranText; header=default_header(), binary=false)
write_mmn(filename; M, kpb_k, kpb_G, ::FortranBinaryStream; header=default_header(), binary=false)
```

wannier90 `mmn` ファイルを書く。

# 引数

  * `filename`: 出力ファイル名
  * `M`: 長さ-`n_kpts` の `n_bands * n_bands * n_bvecs` 配列のベクトル
  * `kpb_k`: 長さ-`n_kpts` の長さ-`n_bvecs` の整数のベクトル
  * `kpb_G`: 長さ-`n_kpts` の長さ-`n_bvecs` の `Vec3{Int}` のベクトル（bベクトル用）

# キーワード引数

  * `header`: ヘッダ文字列
  * `binary`: true の場合、Fortran バイナリ形式で書き込む

1 番目のバージョンは他の 2 つの便利なラッパーです。
