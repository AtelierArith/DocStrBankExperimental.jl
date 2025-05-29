```
flux_nonconservative_powell(u_ll, u_rr, orientation::Integer,
                            equations::IdealGlmMhdMulticomponentEquations2D)
```

非対称の二点フラックスが、Powellの非保存（ソース）項と、[`IdealGlmMhdMulticomponentEquations2D`](@ref)のGLM乗数に関連するガリレオ非保存項を離散化します。

## 参考文献

  * Marvin Bohm, Andrew R.Winters, Gregor J. Gassner, Dominik Derigs, Florian Hindenlang, Joachim Saur 抵抗性MHD方程式のエントロピー安定ノード不連続ガレルキン法。第I部：理論と数値検証 [DOI: 10.1016/j.jcp.2018.06.027](https://doi.org/10.1016/j.jcp.2018.06.027)
