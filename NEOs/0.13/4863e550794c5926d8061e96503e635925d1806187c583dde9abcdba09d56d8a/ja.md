```
RNp1BP_pN_A_J23E_J2S_ng_eph_threads!(dq, q, params, t)
```

近地小惑星動力学モデル（$d = 2$）。モデルで考慮される天体は、太陽、8つの惑星、月、ケレス、および質量ゼロのテスト粒子としての関心のある小惑星です。考慮される動力学的効果は次のとおりです：

  * すべての天体間のポストニュートン点質量加速度： https://ui.adsabs.harvard.edu/abs/1971mfdo.book.....M/abstract のページ7の式（35）を参照してください。
  * 地球の形状効果（扁平率）（$J_2$および$J_3$）、
  * 太陽の$J_2$効果および
  * 月の$J_2$および$J_3$効果： https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract のページ13の式（28）および https://ui.adsabs.harvard.edu/abs/1971mfdo.book.....M/abstract のページ33の式（173）および（174）を参照してください。
  * 地球の向きの歳差と揺動のための運動学モデル（IAU 1976/1980 地球向きモデル）： [`PlanetaryEphemeris.c2t_jpl_de430`](@ref) を参照してください。
  * 月の向きのための運動学モデル（Seidelmann et al., 2006）： https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract のページ9の式（14）-（15）およびページ16の式（34）-（35）を参照してください。
  * 小惑星に作用する非重力加速度：含まれています（ヤルコフスキー効果）

$$
\mathbf{a}_\text{nongrav} = A_2\left(\frac{1 \ \text{au}}{r}\right)^d*\hat{\mathbf{t}},
$$

ここで、$\hat{\mathbf{t}}$は単位太陽中心横ベクトル、$r$は小惑星の太陽中心範囲、$A_2$は係数（単位はau/day^2）、$d = 2$です。

パフォーマンスを向上させるために、一部の内部ループは `Threads.threads for` を介してマルチスレッド化されています。

また、[`PlanetaryEphemeris.NBP_pN_A_J23E_J23M_J2S!`](@ref) も参照してください。
