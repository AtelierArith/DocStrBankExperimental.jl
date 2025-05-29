```
unwrap_laplacian(
    phas::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    solver::Symbol = :mgpcg
) -> typeof(similar(phas))
```

ラプラシアン位相のアンラッピング [1]。

ラプラシアンは、複素位相に対して二次中心差分を使用して計算されます。得られたポアソン方程式は、均質ディリクレ（`solver = :mgpcg`）、ノイマン（`:dct`）、または周期（`:fft`）境界条件（BC）で解くことができます。ノイマンおよび周期BCは配列に課され、ディリクレBCは関心領域（ROI）（`mask`）に課されます。ROIの境界は、外部の値（`mask = 0`）が境界点として、内部の値（`mask = 1`）が内部点として扱われるように設定されます。すなわち、BC: `uphas[!mask] = 0`。この方法は、位相のアンラッピング [1] と調和背景フィールドの除去 [2] を組み合わせたものです。

### 引数

  * `phas::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: ラップされた（マルチエコー）位相
  * `mask::AbstractArray{Bool, 3}`: 関心領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: ボクセルサイズ

### キーワード

  * `solver::Symbol = :mgpcg`: ポアソン方程式のソルバー

      * `:dct`: 配列上の均質ノイマン境界条件
      * `:fft`: 配列上の周期境界条件
      * `:mgpcg`: `mask` 上の均質ディリクレ境界条件（マルチグリッド前処理共役勾配法）

### 戻り値

  * `typeof(similar(phas))`: アンラップされた位相

### 参考文献

[1] Schofield MA, Zhu Y. Fast phase unwrapping algorithm for interferometric     applications. Optics letters. 2003 Jul 15;28(14):1194-6.

[2] Zhou D, Liu T, Spincemaille P, Wang Y. Background field removal by solving     the Laplacian boundary value problem. NMR in Biomedicine. 2014 Mar;27(3):312-9.
