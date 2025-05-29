```
Gb_Choudhury(; leafwidth, LAI, wind_zh, constants)
Gb_Choudhury!(df; leafwidth, LAI, wind_zh, constants)
```

Choudhury & Monteith 1988 に従った熱伝達のためのキャノピー境界層伝導率を推定します。

# 引数

  * `df`               : `Gb_h` を追加/更新する DataFrame
  * `leafwidth`        : 葉の幅 (m)
  * `LAI`              : 一側葉面積指数
  * `wind_zh`          : キャノピー高さでの風速 (m s-1)、[`wind_profile`](@ref) を参照
  * `constants=`[`BigleafConstants`](@ref)`()`

# 値

[`compute_Gb!`](@ref) を参照

# 詳細

Choudhury & Monteith 1988 に従った境界層伝導率は次のように与えられます：

$$
Gb_h = LAI \left( 2a/\alpha \sqrt{u(z_h)/w} (1-e^{-\alpha/2})\right)
$$

ここで、$\alpha$ は LAI に対する経験的関係としてモデル化されています (McNaughton & van den Hurk 1995):

$$
\alpha = 4.39 - 3.97 e^{-0.258 \, LAI}
$$

$$
w
$$

は葉の幅で、$u(zh)$ はキャノピー表面での風速です。

これは、センサー高さ zr で測定された風速と風の消失係数 $\alpha$ から近似できます：$u(z_h) = u(z_r) / e^{\alpha(z_r/z_h -1)}$。ただし、ここでは（明示的に与えられていない場合）[`wind_profile`](@ref) によって推定されます。

# 参考文献

  * Choudhury, B. J., Monteith J_L., 1988: A four-layer model for the heat budget of homogeneous land surfaces. Q. J. R. Meteorol. Soc. 114, 373-398.
  * McNaughton, K. G., Van den Hurk, B*J*J_M., 1995: A 'Lagrangian' revision of the resistors in the two-layer model for calculating the energy budget of a plant canopy. Boundary-Layer Meteorology 74, 261-288.
  * Hicks, B*B., Baldocchi, D*D., Meyers, T*P., Hosker, J*R., Matt, D_R., 1987: A preliminary multiple resistance routine for deriving dry deposition velocities from measured quantities. Water, Air, and Soil Pollution 36, 311-330.
