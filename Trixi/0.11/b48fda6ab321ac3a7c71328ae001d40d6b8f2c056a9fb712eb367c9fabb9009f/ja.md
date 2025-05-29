```
flux_nonconservative_powell_local_symmetric(u_ll, orientation::Integer,
                                            equations::IdealGlmMhdEquations2D,
                                            nonconservative_type::NonConservativeSymmetric,
                                            nonconservative_term::Integer)
```

PowellおよびGLM非保守項の対称部分。サブセル制限のための非保守的なスタガード「フラックス」の計算に必要です。例えば、

  * Rueda-Ramírez, Gassner (2023). A Flux-Differencing Formula for Split-Form Summation By Parts Discretizations of Non-Conservative Systems. https://arxiv.org/pdf/2211.14009.pdf.

この関数は、dg*2d*subcell_limiters.jlでサブセルフラックスを計算するために使用されます。
