```
source_terms_eoc_test_euler(u, x, t, equations::CompressibleEulerEquations3D)
```

自己重力を用いたオイラー方程式の収束テストに使用されるセットアップ

  * Michael Schlottke-Lakemper, Andrew R. Winters, Hendrik Ranocha, Gregor J. Gassner (2020) 自己重力ガス動力学のための純粋に双曲的な不連続ガレルキンアプローチ [arXiv: 2008.10593](https://arxiv.org/abs/2008.10593)

[`initial_condition_eoc_test_coupled_euler_gravity`](@ref) と組み合わせて使用されます。

!!! note
    このメソッドは、解析的自己重力を持つ純粋なオイラーシミュレーションのテストに使用されます。オイラー-重力の結合シミュレーションを行う場合は、代わりに [`source_terms_eoc_test_coupled_euler_gravity`](@ref) を使用する必要があります。

