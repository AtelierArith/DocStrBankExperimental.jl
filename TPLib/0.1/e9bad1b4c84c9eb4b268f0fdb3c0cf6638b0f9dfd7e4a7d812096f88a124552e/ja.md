```
compute_ext_rays(I::Matrix{<:SemiRing}, n::Integer)
compute_ext_rays(I::Matrix{<:Number}, n::Integer, semiring=:max)
```

与えられた不等式 `I` によって定義される熱帯円錐の極端な光線の集合を次元 `n` で計算します。各行の `I` には `2n` の係数が含まれています。これを $[a_{i1} \, \dots \, a_{in} \, b_{i1} \, \dots \, b_{in}]$ と書くと、次の熱帯不等式を表します。

$$
\max(a_{i1} + x_1, \dots, a_{in} + x_n) \geqslant \max(b_{i1} + x_1, \dots, b_{in} + x_n)
$$

`I` の係数が `MaxPlus{T}` または `MinPlus{T}` 型である場合、計算はそれぞれ max-plus または min-plus 熱帯半環で行われます。そうでない場合、係数を半環 `:max` または `:min` に変換するかどうかを指定できます。すべての行が円錐を生成する熱帯点である行列 `G::Matrix{<:SemiRing}` を返します。

# 参考文献

[1] X. Allamigeon. Static analysis of memory manipulations by abstract interpretation – Algorithmics of tropical polyhedra, and application to abstract interpretation. PhD thesis. 

[2] X. Allamigeon, S. Gaubert, E. Goubault. Computing the vertices of tropical polyhedra using directed hypergraphs. Discrete & Computational Geometry, 49(2):247–279, 2013. E-print arXiv:0904.3436v4.
