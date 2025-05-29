```julia
write_bxsf(filename, fermi_energy, origin, span_vectors, E)

```

`bxsf`ファイルを書き込みます。

# 引数

  * `fermi_energy`: Fermiエネルギー（eV）
  * `origin`: `3`, Å⁻¹, グリッドの原点
  * `span_vectors`: `3 * 3`, Å⁻¹, 各列はスパンベクトル
  * `E`: `n_bands * nx * ny * nz`, 各グリッド点での固有値
