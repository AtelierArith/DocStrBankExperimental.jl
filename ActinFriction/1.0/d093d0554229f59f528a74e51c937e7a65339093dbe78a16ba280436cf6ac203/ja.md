# アクチンリングダイナミクスシミュレーションパッケージ

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7781755.svg)](https://doi.org/10.5281/zenodo.7781755)

受動的に交差結合されたアクチンリングのダイナミクスをシミュレートするためのJuliaパッケージです。

[リポジトリ](https://github.com/cumberworth/ActinFriction.jl)

[ドキュメント](http://www.cumberworth.org/ActinFriction.jl)

このパッケージは、[Ref. 1](#references)で説明されているSDEを解くことを可能にし、同じ論文で説明されている摩擦係数を直接計算するためのメソッドを提供します。

## インストール

パッケージは、Julia REPLを起動し、`]`を入力してパッケージモードに入り、次のコマンドを実行することでインストールできます。

```
add ActinFriction
```

Generalレジストリからインストールする場合、または次のコマンドを実行して開発リポジトリから直接インストールすることもできます。

```
add https://github.com/cumberworth/ActinFriction.jl
```

関連するPythonパッケージ、[actinfrictionpy](https://github.com/cumberworth/actinfrictionpy)には、これらの出力を分析およびプロットするためのコードが含まれています...

## 参考文献

[1] A. Cumberworth and P. R. ten Wolde, 受動的交差結合剤によるアクチンリングの収縮, [arXiv:2203.04260 [physics.bio-ph]](https://doi.org/10.48550/arXiv.2203.04260).

## リンク

[Juliaプログラミング言語](https://julialang.org/)

[プロットパッケージ](https://github.com/cumberworth/actinfrictionpy)

[複製パッケージ Ref. 1](https://doi.org/10.5281/zenodo.6327217)

  * [`R_to_lambda`](@ref)
  * [`RingParams`](@ref)
  * [`bending_force`](@ref)
  * [`condensation_force`](@ref)
  * [`entropic_force`](@ref)
  * [`equilibrium_occupancy`](@ref)
  * [`equilibrium_ring_radius`](@ref)
  * [`force_L_to_R`](@ref)
  * [`free_energy_barrier_Nd_exact`](@ref)
  * [`free_energy_barrier_Nd_exp`](@ref)
  * [`free_energy_barrier_cX`](@ref)
  * [`friction_coefficient_Nd_exact`](@ref)
  * [`friction_coefficient_Nd_exp`](@ref)
  * [`friction_coefficient_cX`](@ref)
  * [`kramers_r0`](@ref)
  * [`l_to_lambda`](@ref)
  * [`lambda_to_R`](@ref)
  * [`lambda_to_l`](@ref)
  * [`savename`](@ref)
  * [`solve_and_write_ring_Nd_contin_exp`](@ref)
  * [`solve_and_write_ring_Nd_contin_exp_noise`](@ref)
  * [`solve_and_write_ring_Nd_discrete_exact`](@ref)
  * [`solve_and_write_ring_Nd_discrete_exact_noise`](@ref)
  * [`solve_and_write_ring_Nd_discrete_exp`](@ref)
  * [`solve_and_write_ring_Nd_discrete_exp_noise`](@ref)
  * [`solve_and_write_ring_cX`](@ref)
  * [`solve_and_write_ring_cX_noise`](@ref)
