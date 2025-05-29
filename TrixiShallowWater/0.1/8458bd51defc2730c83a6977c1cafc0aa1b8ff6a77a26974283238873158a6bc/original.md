```
ShieldsStressModel(; m_1, m_2, m_3, k_1, k_2, k_3, theta_c, d_s)
```

Create a Shields stress model to compute the sediment discharge `q_s` based on the generalized formulation from equation (1.2) in the given reference.

The choice of the real constants `m_1`, `m_2`, `m_3`, `k_1`, `k_2`, and `k_3` creates different models. For example, setting `m_1=0`, `m_2=1.5`, `m_3=0`, `k_1=8`, `k_2=1`, and `k_3=0` yields the sedimentation model of Meyer-Peter and Müller as given in [`MeyerPeterMueller`](@ref) below. The Shields stress represents the ratio of agitating and stabilizing forces in the sediment bed where `theta_c` is the critical Shields stress for incipient motion and `d_s` is the mean diameter of the sediment grain size.

  * E.D. Fernández-Nieto, T.M. de Luna, G. Narbona-Reina and J. de Dieu Zabsonré (2017)
    Formal deduction of the Saint-Venant–Exner model including arbitrarily sloping sediment beds and associated energy
    [DOI: 10.1051/m2an/2016018](https://doi.org/10.1051/m2an/2016018)
