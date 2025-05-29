```
boundary_condition_slip_wall(u_inner, normal_direction, x, t, surface_flux_function,
                             equations::AcousticPerturbationEquations2D)
```

摂動した速度の直交射影を使用して、境界状態での接線速度の可能性を保持しながら、法線速度をゼロにします。詳細は以下の論文にあります：

  * Marcus Bauer, Jürgen Dierke and Roland Ewert (2011) Application of a discontinuous Galerkin method to discretize acoustic perturbation equations [DOI: 10.2514/1.J050333](https://doi.org/10.2514/1.J050333)
