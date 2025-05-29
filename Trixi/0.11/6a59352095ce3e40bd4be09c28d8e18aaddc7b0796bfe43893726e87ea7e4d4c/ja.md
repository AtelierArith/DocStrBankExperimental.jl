```
initial_condition_eoc_test_coupled_euler_gravity(x, t, equations::CompressibleEulerEquations1D)
```

自己重力を持つオイラー方程式の収束テストに使用されるセットアップの一次元バリアント

  * Michael Schlottke-Lakemper, Andrew R. Winters, Hendrik Ranocha, Gregor J. Gassner (2020) 自己重力を持つガス動力学のための純粋に双曲的な不連続ガレルキンアプローチ [arXiv: 2008.10593](https://arxiv.org/abs/2008.10593)

!!! note
    一次元の空間において製造された解に必要な追加のソース項はありません。したがって、[`source_terms_eoc_test_coupled_euler_gravity`](@ref) はそこには存在しません。

