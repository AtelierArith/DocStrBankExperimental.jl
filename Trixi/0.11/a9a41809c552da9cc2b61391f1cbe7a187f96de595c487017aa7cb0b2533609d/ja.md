```
flux_nonconservative_wintermeyer_etal(u_ll, u_rr, orientation::Integer,
                                      equations::ShallowWaterEquations1D)
```

非対称の二点体積フラックスで、底面地形の勾配を含む非保守（ソース）項を離散化します [`ShallowWaterEquations1D`](@ref)。

[`flux_wintermeyer_etal`](@ref) と組み合わせることで、体積と表面の両方でエントロピー保存とバランスの良さを提供します。

さらなる詳細は以下の論文にあります：

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner and David A. Kopriva (2017) エントロピー安定ノード不連続ガレルキン法による、非構造的曲線メッシュ上の二次元浅水方程式のための底面地形が不連続な場合の研究 [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
  * Patrick Ersing, Andrew R. Winters (2023) 曲線メッシュ上の二層浅水方程式のためのエントロピー安定不連続ガレルキン法に関する研究 [DOI: 10.48550/arXiv.2306.12699](https://doi.org/10.48550/arXiv.2306.12699)
