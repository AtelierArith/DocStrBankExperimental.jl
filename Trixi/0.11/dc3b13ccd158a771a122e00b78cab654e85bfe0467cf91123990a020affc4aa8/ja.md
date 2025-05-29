```
flux_nonconservative_powell(u_ll, u_rr, orientation::Integer,
                            equations::IdealGlmMhdEquations3D)
flux_nonconservative_powell(u_ll, u_rr,
                            normal_direction::AbstractVector,
                            equations::IdealGlmMhdEquations3D)
```

ポウェルの非保守（ソース）項と、[`IdealGlmMhdEquations3D`](@ref)のGLM乗数に関連するガリレイ非保守項を離散化する非対称二点フラックス。

曲線メッシュでは、メトリクスのデイリアシングのために平均法線方向を使用するため、実装が参照と異なります。

## 参考文献

  * Marvin Bohm, Andrew R.Winters, Gregor J. Gassner, Dominik Derigs, Florian Hindenlang, Joachim Saur 抵抗性MHD方程式のエントロピー安定ノード不連続ガレルキン法。第I部：理論と数値検証 [DOI: 10.1016/j.jcp.2018.06.027](https://doi.org/10.1016/j.jcp.2018.06.027)
