## `score` (VolumeFraction)

```julia
score(vol::AbstractArray, hu_calcium, hu_heart_tissue, alg::VolumeFraction)

score(vol::AbstractArray, hu_calcium, hu_heart_tissue, voxel_size, alg::VolumeFraction)

score(vol::AbstractArray, hu_calcium, hu_heart_tissue, voxel_size, density_calcium, alg::VolumeFraction)

score(vol::AbstractMatrix, hu_calcium, hu_heart_tissue, alg::VolumeFraction)

score(vol::AbstractMatrix, hu_calcium, hu_heart_tissue, voxel_size, alg::VolumeFraction)

score(vol::AbstractMatrix, hu_calcium, hu_heart_tissue, voxel_size, density_calcium, alg::VolumeFraction)
```

提供された引数に応じて、石灰化されたボクセルの数、石灰化の体積、または石灰化の質量を計算します。

#### 入力

  * `vol`: 潜在的なカルシウムを含む関心領域。
  * `hu_calcium`: 知られているカルシウム密度に関連するハウンスフィールド単位。
  * `hu_heart_tissue`: 背景心臓組織に関連するハウンスフィールド単位。
  * `voxel_size`: （オプション）個々のピクセル/ボクセルのサイズ。
  * `density_calcium`: （オプション）前述のカルシウムの密度。
  * `alg::VolumeFraction`: 計算に使用されるアルゴリズム。

#### 戻り値

  * `vol`、`hu_calcium`、`hu_heart_tissue`、および `alg` で呼び出された場合、この関数は石灰化されたボクセルの数を計算して返します。
  * `vol`、`hu_calcium`、`hu_heart_tissue`、`voxel_size`、および `alg` で呼び出された場合、この関数は石灰化の体積を計算して返します。
  * `vol`、`hu_calcium`、`hu_heart_tissue`、`voxel_size`、`density_calcium`、および `alg` で呼び出された場合、この関数は石灰化の質量を計算して返します。

#### 参考文献

[Coronary artery calcium mass measurement based on integrated intensity and volume fraction techniques](https://doi.org/10.1101/2023.01.12.23284482)
