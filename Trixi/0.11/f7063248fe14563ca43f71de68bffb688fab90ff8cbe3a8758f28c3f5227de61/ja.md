```
source_terms_eoc_test_coupled_euler_gravity(u, x, t, equations::CompressibleEulerEquations3D)
```

自己重力を持つオイラー方程式の収束テストに使用されるセットアップ

  * Michael Schlottke-Lakemper, Andrew R. Winters, Hendrik Ranocha, Gregor J. Gassner (2020) 自己重力を持つガス動力学のための純粋に双曲的な不連続ガレルキンアプローチ [arXiv: 2008.10593](https://arxiv.org/abs/2008.10593)

[`initial_condition_eoc_test_coupled_euler_gravity`](@ref) と組み合わせて。
