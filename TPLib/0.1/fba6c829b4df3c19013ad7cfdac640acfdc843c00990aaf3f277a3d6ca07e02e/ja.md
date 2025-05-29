```
compute_ext_rays_polar(M::Matrix{<:SemiRing}, n::Integer)
compute_ext_rays_polar(M::Matrix{<:Number}, n::Integer, semiring=:max)
```

極コーンの極の極端なレイの集合を、次元 `n` の生成集合 `M` によって計算します。各行は `M` の `n` の係数を含み、熱帯コーンの生成子を表します。`M` の係数が `MaxPlus{T}` または `MinPlus{T}` の型である場合、計算はそれぞれ max-plus または min-plus 熱帯半環で行われます。そうでない場合、係数を半環 `:max` または `:min` に変換するかどうかを指定できます。すべての行が極コーンを生成する熱帯点である行列 `::Matrix{<:SemiRing}` を返します。

# 参考文献

[1] X. Allamigeon, S. Gaubert, and R. D. Katz. Tropical polar cones, hypergraph transversals, and mean payoff games. Linear Algebra Appl., 435(7):1549–1574, 2011. E-print arXiv:1004.2778.
