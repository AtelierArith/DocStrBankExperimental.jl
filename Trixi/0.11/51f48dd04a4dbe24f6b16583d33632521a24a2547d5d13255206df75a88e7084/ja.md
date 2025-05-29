```
min_max_speed_einfeldt(u_ll, u_rr, orientation::Integer, equations)
min_max_speed_einfeldt(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

より高度な最小および最大波速計算は、以下に基づいています。

  * Bernd Einfeldt (1988) On Godunov-type methods for gas dynamics. [DOI: 10.1137/0725021](https://doi.org/10.1137/0725021)
  * Bernd Einfeldt, Claus-Dieter Munz, Philip L. Roe and Björn Sjögreen (1991) On Godunov-type methods near low densities. [DOI: 10.1016/0021-9991(91)90211-3](https://doi.org/10.1016/0021-9991(91)90211-3)

元々は圧縮性オイラー方程式のために開発されました。コンパクトな表現は[この講義ノート、eq. (9.28)](https://metaphor.ethz.ch/x/2019/hs/401-4671-00L/literature/mishra_hyperbolic_pdes.pdf)に見つけることができます。

また、[`FluxHLL`](@ref)、[`min_max_speed_naive`](@ref)、[`min_max_speed_davis`](@ref)も参照してください。
