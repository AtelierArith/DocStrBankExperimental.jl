```
flux_nonconservative_chan_etal(u_ll, u_rr, orientation::Integer,
                               equations::CompressibleEulerEquationsQuasi1D)
flux_nonconservative_chan_etal(u_ll, u_rr, normal_direction, 
                               equations::CompressibleEulerEquationsQuasi1D)
flux_nonconservative_chan_etal(u_ll, u_rr, normal_ll, normal_rr,
                               equations::CompressibleEulerEquationsQuasi1D)
```

非対称の二点体積フラックスは、圧力の勾配を含む非保守的（ソース）項を離散化し、[`CompressibleEulerEquationsQuasi1D`](@ref) とノズル幅を考慮しています。

さらなる詳細は、以下の論文にあります：

  * Jesse Chan, Khemraj Shukla, Xinhui Wu, Ruofeng Liu, Prani Nalluri (2023)   高次エントロピー安定スキームによる準1次元浅水方程式と圧縮性オイラー方程式   [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)
