```
flux_nonconservative_chan_etal(u_ll, u_rr, orientation::Integer,
                               equations::ShallowWaterEquationsQuasi1D)
flux_nonconservative_chan_etal(u_ll, u_rr, normal_direction::AbstractVector,
                               equations::ShallowWaterEquationsQuasi1D)    
flux_nonconservative_chan_etal(u_ll, u_rr, 
                               normal_ll::AbstractVector, normal_rr::AbstractVector,
                               equations::ShallowWaterEquationsQuasi1D)
```

非対称の二点体積フラックスは、底面地形の勾配を含む非保守（ソース）項を離散化し、[`ShallowWaterEquationsQuasi1D`](@ref) とチャネル幅を考慮しています。

さらなる詳細は、以下の論文にあります：

  * Jesse Chan, Khemraj Shukla, Xinhui Wu, Ruofeng Liu, Prani Nalluri (2023)   高次エントロピー安定スキームによる準1次元浅水方程式と圧縮可能なオイラー方程式   [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)
