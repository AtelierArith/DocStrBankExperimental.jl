`WannierIO.jl`: Wannier90ファイルフォーマットの読み書き用パッケージ。

---

# WannierIO.jl

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://io.wannierjl.org/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://io.wannierjl.org/dev) [![CI](https://github.com/qiaojunfeng/WannierIO.jl/workflows/CI/badge.svg)](https://github.com/qiaojunfeng/WannierIO.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/qiaojunfeng/WannierIO.jl/branch/main/graph/badge.svg?token=F7Tl05iVW9)](https://codecov.io/gh/qiaojunfeng/WannierIO.jl)

[Wannier90](https://github.com/wannier-developers/wannier90)ファイルフォーマットの読み書き用のJuliaパッケージです。

このパッケージは、他のパッケージでの再利用を容易にするために、ミニマリスティックに設計されています。

## クイック例

```julia
using WannierIO

A = read_amn("silicon.amn")
write_amn("silicon_2.amn", A)

chk = read_chk("silicon.chk")
write_chk("silicon_2.chk", chk; binary=true)
```

## 関連パッケージ

  * [Wannier.jl](https://github.com/qiaojunfeng/Wannier.jl): Wannier化およびWannier補間。`Wannier.jl`のIO部分は分離され、このパッケージに移動されました。

---

エクスポートされた関数:

  * [`get_U`](@ref)
  * [`get_Udis`](@ref)
  * [`read_amn`](@ref)
  * [`read_bxsf`](@ref)
  * [`read_chk`](@ref)
  * [`read_cube`](@ref)
  * [`read_eig`](@ref)
  * [`read_mmn`](@ref)
  * [`read_nnkp`](@ref)
  * [`read_spn`](@ref)
  * [`read_uHu`](@ref)
  * [`read_uIu`](@ref)
  * [`read_unk`](@ref)
  * [`read_w90_band`](@ref)
  * [`read_w90_band_dat`](@ref)
  * [`read_w90_band_kpt`](@ref)
  * [`read_w90_band_labelinfo`](@ref)
  * [`read_w90_hrdat`](@ref)
  * [`read_w90_rdat`](@ref)
  * [`read_w90_tbdat`](@ref)
  * [`read_w90_wsvec`](@ref)
  * [`read_win`](@ref)
  * [`read_wout`](@ref)
  * [`read_xsf`](@ref)
  * [`write_amn`](@ref)
  * [`write_bxsf`](@ref)
  * [`write_chk`](@ref)
  * [`write_cube`](@ref)
  * [`write_eig`](@ref)
  * [`write_mmn`](@ref)
  * [`write_nnkp`](@ref)
  * [`write_spn`](@ref)
  * [`write_uHu`](@ref)
  * [`write_uIu`](@ref)
  * [`write_unk`](@ref)
  * [`write_w90_band`](@ref)
  * [`write_w90_band_dat`](@ref)
  * [`write_w90_band_kpt`](@ref)
  * [`write_w90_band_labelinfo`](@ref)
  * [`write_w90_hrdat`](@ref)
  * [`write_w90_rdat`](@ref)
  * [`write_w90_tbdat`](@ref)
  * [`write_w90_wsvec`](@ref)
  * [`write_win`](@ref)
  * [`write_xsf`](@ref)
