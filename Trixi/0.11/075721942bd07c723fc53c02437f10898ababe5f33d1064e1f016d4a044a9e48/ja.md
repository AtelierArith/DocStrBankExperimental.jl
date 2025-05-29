```
flux_shima_etal(u_ll, u_rr, orientation_or_normal_direction,
                equations::CompressibleEulerEquations2D)
```

このフラックスは、元の運動エネルギー保存の二点フラックスの修正です。

  * Yuichi Kuya, Kosuke Totani, Soshi Kawai (2018) Kinetic energy and entropy preserving schemes for compressible flows by split convective forms [DOI: 10.1016/j.jcp.2018.08.058](https://doi.org/10.1016/j.jcp.2018.08.058)

修正はエネルギーフラックスにあり、圧力平衡を保証するために行われ、以下によって開発されました。

  * Nao Shima, Yuichi Kuya, Yoshiharu Tamaki, Soshi Kawai (JCP 2020) Preventing spurious pressure oscillations in split convective form discretizations for compressible flows [DOI: 10.1016/j.jcp.2020.110060](https://doi.org/10.1016/j.jcp.2020.110060)
