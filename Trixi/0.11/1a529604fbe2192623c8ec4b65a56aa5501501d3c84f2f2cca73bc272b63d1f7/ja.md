@inline function flux*chan*etal(u*ll, u*rr, orientation::Integer,                                            equations::CompressibleEulerEquationsQuasi1D)

保守的（対称的）部分のエントロピー保存フラックスは、準1D圧縮オイラー方程式の分割形式です。このフラックスは、[`CompressibleEulerEquations1D`](@ref)のための[`flux_ranocha`](@ref)の一般化です。さらなる詳細は以下の論文にあります：

  * Jesse Chan, Khemraj Shukla, Xinhui Wu, Ruofeng Liu, Prani Nalluri (2023)  高次エントロピー安定スキームの準1次元浅水および圧縮オイラー方程式 [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)
