```
flux_nonconservative_fjordholm_etal(u_ll, u_rr, orientation::Integer,
                                    equations::ShallowWaterEquations1D)
```

非対称の二点表面フラックスは、底面地形の勾配を含む非保守的（ソース）項を離散化します [`ShallowWaterEquations1D`](@ref)。

このフラックスは、エントロピー保存とバランスの良さを確保するために、インターフェースで [`flux_fjordholm_etal`](@ref) と一緒に使用できます。

元の有限体積定式化に関する詳細は以下にあります。

  * Ulrik S. Fjordholm, Siddhartha Mishra, Eitan Tadmor (2011) 不連続な地形を持つ浅水方程式のためのバランスの取れたエネルギー安定スキーム [DOI: 10.1016/j.jcp.2011.03.042](https://doi.org/10.1016/j.jcp.2011.03.042)

および曲線状の2Dケースについては、以下の論文に記載されています。

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner, David A. Kopriva (2017) 不連続な水深を持つ非構造的曲線メッシュ上の二次元浅水方程式のためのエントロピー安定ノード不連続ガレルキン法 [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
